---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 04e9e47055610ef8120b44f2418a0843e5901062
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262556"
---
# <span data-ttu-id="80f3a-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="80f3a-103">Test-Connection</span></span>

## <span data-ttu-id="80f3a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="80f3a-104">SYNOPSIS</span></span>
<span data-ttu-id="80f3a-105">Skickar ICMP Echo Request-paket, eller pingar, till en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="80f3a-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="80f3a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="80f3a-106">SYNTAX</span></span>

### <span data-ttu-id="80f3a-107">DefaultPing (standard)</span><span class="sxs-lookup"><span data-stu-id="80f3a-107">DefaultPing (Default)</span></span>

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="80f3a-108">RepeatPing</span><span class="sxs-lookup"><span data-stu-id="80f3a-108">RepeatPing</span></span>

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="80f3a-109">MtuSizeDetect</span><span class="sxs-lookup"><span data-stu-id="80f3a-109">MtuSizeDetect</span></span>

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="80f3a-110">TraceRoute</span><span class="sxs-lookup"><span data-stu-id="80f3a-110">TraceRoute</span></span>

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="80f3a-111">TcpPort</span><span class="sxs-lookup"><span data-stu-id="80f3a-111">TcpPort</span></span>

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="80f3a-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="80f3a-112">DESCRIPTION</span></span>

<span data-ttu-id="80f3a-113">`Test-Connection`Cmdleten skickar Internet Control Message Protocol (ICMP) eko begär paket, eller pingar, till en eller flera fjärrdatorer och returnerar svars Svaren för eko.</span><span class="sxs-lookup"><span data-stu-id="80f3a-113">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="80f3a-114">Du kan använda den här cmdleten för att avgöra om en viss dator kan kontaktas i ett IP-nätverk.</span><span class="sxs-lookup"><span data-stu-id="80f3a-114">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="80f3a-115">Du kan använda parametrarna för `Test-Connection` för att ange både sändnings-och mottagnings datorer, köra kommandot som ett bakgrunds jobb för att ange ett timeout-värde och antalet pingar och för att konfigurera anslutningen och autentiseringen.</span><span class="sxs-lookup"><span data-stu-id="80f3a-115">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="80f3a-116">Till skillnad från det välkända **ping** -kommandot `Test-Connection` returnerar ett **TestConnectionCommand + PingStatus** -objekt som du kan undersöka i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80f3a-116">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="80f3a-117">Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt för varje testad anslutning.</span><span class="sxs-lookup"><span data-stu-id="80f3a-117">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="80f3a-118">Om flera anslutningar testas returneras en matris med **booleska** värden.</span><span class="sxs-lookup"><span data-stu-id="80f3a-118">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="80f3a-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="80f3a-119">EXAMPLES</span></span>

### <span data-ttu-id="80f3a-120">Exempel 1: skicka eko förfrågningar till en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="80f3a-120">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="80f3a-121">Det här exemplet skickar eko begär ande paket från den lokala datorn till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="80f3a-121">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
   Destination: Server01

Ping Source           Address                   Latency BufferSize Status
                                                   (ms)        (B)
---- ------           -------                   ------- ---------- ------
   1 ADMIN1           10.59.137.44                   24         32 Success
   2 ADMIN1           10.59.137.44                   39         32 Success
   3 ADMIN1           *                               *          * TimedOut
   4 ADMIN1           10.59.137.44                   28         32 Success
```

<span data-ttu-id="80f3a-122">`Test-Connection` använder parametern **TargetName** för att ange Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="80f3a-122">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="80f3a-123">**IPv4** -parametern anger protokollet för testet.</span><span class="sxs-lookup"><span data-stu-id="80f3a-123">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="80f3a-124">En serie med **TestConnectionCommand + PingStatus** -objekt skickas till utdataströmmen, ett objekt per ping-svar från mål datorn.</span><span class="sxs-lookup"><span data-stu-id="80f3a-124">A series of **TestConnectionCommand+PingStatus** objects are sent to the output stream, one object per ping reply from the target machine.</span></span>

### <span data-ttu-id="80f3a-125">Exempel 2: skicka eko förfrågningar till flera datorer</span><span class="sxs-lookup"><span data-stu-id="80f3a-125">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="80f3a-126">I det här exemplet skickas pingar från den lokala datorn till flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="80f3a-126">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="80f3a-127">Exempel 3: Använd parametrar för att anpassa test kommandot</span><span class="sxs-lookup"><span data-stu-id="80f3a-127">Example 3: Use parameters to customize the test command</span></span>

<span data-ttu-id="80f3a-128">I det här exemplet används parametrarna för `Test-Connection` för att anpassa kommandot.</span><span class="sxs-lookup"><span data-stu-id="80f3a-128">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="80f3a-129">Den lokala datorn skickar ett ping-test till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="80f3a-129">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="80f3a-130">`Test-Connection` använder parametern **TargetName** för att ange Server01.</span><span class="sxs-lookup"><span data-stu-id="80f3a-130">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="80f3a-131">Parametern **Count** anger att tre pingar skickas till Server01-datorn med en **fördröjning** på 2 sekunders intervall.</span><span class="sxs-lookup"><span data-stu-id="80f3a-131">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="80f3a-132">Du kan använda dessa alternativ när ping-svaret förväntas ta längre tid än vanligt, antingen på grund av ett utökat antal hopp eller ett nätverks tillstånd med hög trafik.</span><span class="sxs-lookup"><span data-stu-id="80f3a-132">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="80f3a-133">Exempel 4: kör ett test som bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="80f3a-133">Example 4: Run a test as a background job</span></span>

<span data-ttu-id="80f3a-134">Det här exemplet visar hur du kör ett `Test-Connection` kommando som ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="80f3a-134">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

<span data-ttu-id="80f3a-135">`Start-Job`Kommandot använder `Test-Connection` cmdleten för att pinga många datorer i ett företag.</span><span class="sxs-lookup"><span data-stu-id="80f3a-135">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="80f3a-136">Värdet för parametern **TargetName** är ett `Get-Content` kommando som läser en lista med dator namn från `Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="80f3a-136">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="80f3a-137">Kommandot använder `Start-Job` cmdleten för att köra kommandot som ett bakgrunds jobb och det sparar jobbet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="80f3a-137">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="80f3a-138">`Receive-Job`Kommandot instrueras `-Wait` tills jobbet har slutförts och hämtar sedan resultaten och lagrar dem i `$Results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="80f3a-138">The `Receive-Job` command is instructed to `-Wait` until the job is completed, and then gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="80f3a-139">Exempel 5: skapa endast en session om ett anslutnings test lyckas</span><span class="sxs-lookup"><span data-stu-id="80f3a-139">Example 5: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="80f3a-140">I det här exemplet skapas en session på Server01-datorn endast om minst en av pingarna som skickats till datorn lyckas.</span><span class="sxs-lookup"><span data-stu-id="80f3a-140">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

<span data-ttu-id="80f3a-141">`Test-Connection`Cmdlet: en pingar `Server01` datorn med parametern **quiet** angiven.</span><span class="sxs-lookup"><span data-stu-id="80f3a-141">The `Test-Connection` cmdlet pings the `Server01` computer, with the **Quiet** parameter provided.</span></span>
<span data-ttu-id="80f3a-142">Det resulterande värdet är `$True` om någon av de fyra pingarna lyckas.</span><span class="sxs-lookup"><span data-stu-id="80f3a-142">The resulting value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="80f3a-143">Om inget av pingarna lyckas är värdet `$False` .</span><span class="sxs-lookup"><span data-stu-id="80f3a-143">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="80f3a-144">Om `Test-Connection` kommandot returnerar ett värde av `$True` använder kommandot `New-PSSession` cmdleten för att skapa **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="80f3a-144">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span>

### <span data-ttu-id="80f3a-145">Exempel 6: Använd parametern traceroute</span><span class="sxs-lookup"><span data-stu-id="80f3a-145">Example 6: Use the Traceroute parameter</span></span>

<span data-ttu-id="80f3a-146">**Traceroute** -parametern har introducerats i PowerShell 6,0 och mappar en väg mellan den lokala datorn och fjärrdestinationen som du anger med parametern **TargetName** .</span><span class="sxs-lookup"><span data-stu-id="80f3a-146">Introduced in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

```powershell
Test-Connection -TargetName www.google.com -Traceroute
```

```Output
   Target: google.com

Hop Hostname                  Ping Latency Status           Source       TargetAddress
                                      (ms)
--- --------                  ---- ------- ------           ------       -------------
  1 172.20.0.1                   1       4 Success          Lira         172.217.9.174
  1 172.20.0.1                   2       3 Success          Lira         172.217.9.174
  1 172.20.0.1                   3       2 Success          Lira         172.217.9.174
  2 12.108.153.193               1       3 Success          Lira         172.217.9.174
  2 12.108.153.193               2       3 Success          Lira         172.217.9.174
  2 12.108.153.193               3       2 Success          Lira         172.217.9.174
  3 12.244.85.177                1      11 Success          Lira         172.217.9.174
  3 12.244.85.177                2      12 Success          Lira         172.217.9.174
  3 12.244.85.177                3      12 Success          Lira         172.217.9.174
  4 *                            1      14 DestinationNetw… Lira         172.217.9.174
  4 *                            2       * TimedOut         Lira         172.217.9.174
  4 *                            3      20 DestinationNetw… Lira         172.217.9.174
  5 *                            1       * TimedOut         Lira         172.217.9.174
  5 *                            2      15 DestinationNetw… Lira         172.217.9.174
  5 *                            3       * TimedOut         Lira         172.217.9.174
  6 *                            1      18 DestinationNetw… Lira         172.217.9.174
  6 *                            2       * TimedOut         Lira         172.217.9.174
  6 *                            3      16 DestinationNetw… Lira         172.217.9.174
  7 *                            1       * TimedOut         Lira         172.217.9.174
  7 *                            2       * TimedOut         Lira         172.217.9.174
  7 *                            3       * TimedOut         Lira         172.217.9.174
  8 *                            1       * TimedOut         Lira         172.217.9.174
  8 *                            2       * TimedOut         Lira         172.217.9.174
  8 *                            3       * TimedOut         Lira         172.217.9.174
  9 *                            1       * TimedOut         Lira         172.217.9.174
  9 *                            2       * TimedOut         Lira         172.217.9.174
  9 *                            3       * TimedOut         Lira         172.217.9.174
 10 *                            1       * TimedOut         Lira         172.217.9.174
 10 *                            2       * TimedOut         Lira         172.217.9.174
 10 *                            3       * TimedOut         Lira         172.217.9.174
 11 172.217.9.174                1      23 Success          Lira         172.217.9.174
 11 172.217.9.174                2      21 Success          Lira         172.217.9.174
 11 172.217.9.174                3      22 Success          Lira         172.217.9.174
```

<span data-ttu-id="80f3a-147">`Test-Connection`Kommandot anropas med parametern **traceroute** .</span><span class="sxs-lookup"><span data-stu-id="80f3a-147">The `Test-Connection` command is called with the **Traceroute** parameter.</span></span> <span data-ttu-id="80f3a-148">Resultaten, som är `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objekt, matas ut till den resulterande utdataströmmen. **Success**</span><span class="sxs-lookup"><span data-stu-id="80f3a-148">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objects, are output to the **Success** output stream.</span></span>

## <span data-ttu-id="80f3a-149">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="80f3a-149">PARAMETERS</span></span>

### <span data-ttu-id="80f3a-150">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="80f3a-150">-BufferSize</span></span>

<span data-ttu-id="80f3a-151">Anger storlek, i byte, för den buffert som skickas med det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="80f3a-151">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="80f3a-152">Standardvärdet är 32.</span><span class="sxs-lookup"><span data-stu-id="80f3a-152">The default value is 32.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-153">-Upprepa</span><span class="sxs-lookup"><span data-stu-id="80f3a-153">-Repeat</span></span>

<span data-ttu-id="80f3a-154">Gör att cmdleten skickar ping-begäranden kontinuerligt.</span><span class="sxs-lookup"><span data-stu-id="80f3a-154">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="80f3a-155">Den här parametern kan inte användas med **Count** -parametern.</span><span class="sxs-lookup"><span data-stu-id="80f3a-155">This parameter can't be used with the **Count** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RepeatPing
Aliases: Continuous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-156">-Antal</span><span class="sxs-lookup"><span data-stu-id="80f3a-156">-Count</span></span>

<span data-ttu-id="80f3a-157">Anger hur många eko-begäranden som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="80f3a-157">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="80f3a-158">Standardvärdet är 4.</span><span class="sxs-lookup"><span data-stu-id="80f3a-158">The default value is 4.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-159">-Fördröjning</span><span class="sxs-lookup"><span data-stu-id="80f3a-159">-Delay</span></span>

<span data-ttu-id="80f3a-160">Anger intervallet mellan pingar, i sekunder.</span><span class="sxs-lookup"><span data-stu-id="80f3a-160">Specifies the interval between pings, in seconds.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-161">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="80f3a-161">-DontFragment</span></span>

<span data-ttu-id="80f3a-162">Den här parametern anger flaggan **Fragmentera inte** i IP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="80f3a-162">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="80f3a-163">Du kan använda den här parametern med parametern **BufferSize** för att testa MTU-storleken för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="80f3a-163">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="80f3a-164">Mer information om MTU för sökvägen finns i artikeln [sökväg för MTU-identifiering](https://wikipedia.org/wiki/Path_MTU_Discovery) i wikipedia.</span><span class="sxs-lookup"><span data-stu-id="80f3a-164">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-165">– IPv4</span><span class="sxs-lookup"><span data-stu-id="80f3a-165">-IPv4</span></span>

<span data-ttu-id="80f3a-166">Tvingar cmdleten att använda IPv4-protokollet för testet.</span><span class="sxs-lookup"><span data-stu-id="80f3a-166">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="80f3a-167">-IPv6</span><span class="sxs-lookup"><span data-stu-id="80f3a-167">-IPv6</span></span>

<span data-ttu-id="80f3a-168">Tvingar cmdleten att använda IPv6-protokollet för testet.</span><span class="sxs-lookup"><span data-stu-id="80f3a-168">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="80f3a-169">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="80f3a-169">-MaxHops</span></span>

<span data-ttu-id="80f3a-170">Anger maximalt antal hopp som ett meddelande om ICMP-begäran kan skickas.</span><span class="sxs-lookup"><span data-stu-id="80f3a-170">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="80f3a-171">Standardvärdet styrs av operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="80f3a-171">The default value is controlled by the operating system.</span></span> <span data-ttu-id="80f3a-172">Standardvärdet för Windows 10 är 128 hopp.</span><span class="sxs-lookup"><span data-stu-id="80f3a-172">The default value for Windows 10 is 128 hops.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-173">-Ping</span><span class="sxs-lookup"><span data-stu-id="80f3a-173">-Ping</span></span>

<span data-ttu-id="80f3a-174">Gör att cmdleten gör ett ping-test.</span><span class="sxs-lookup"><span data-stu-id="80f3a-174">Causes the cmdlet to do a ping test.</span></span> <span data-ttu-id="80f3a-175">Detta är standard läget för `Test-Connection` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="80f3a-175">This is the default mode for the `Test-Connection` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-176">– Tyst</span><span class="sxs-lookup"><span data-stu-id="80f3a-176">-Quiet</span></span>

<span data-ttu-id="80f3a-177">Parametern **quiet** returnerar ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="80f3a-177">The **Quiet** parameter returns a **Boolean** value.</span></span> <span data-ttu-id="80f3a-178">Om du använder den här parametern utelämnas alla fel.</span><span class="sxs-lookup"><span data-stu-id="80f3a-178">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="80f3a-179">Varje anslutning som testas returnerar ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="80f3a-179">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="80f3a-180">Om parametern **TargetName** anger flera datorer returneras en matris med **booleska** värden.</span><span class="sxs-lookup"><span data-stu-id="80f3a-180">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="80f3a-181">Om **ett** ping till ett specifikt mål lyckas `$True` returneras.</span><span class="sxs-lookup"><span data-stu-id="80f3a-181">If **any** ping to a given target succeeds, `$True` is returned.</span></span>

<span data-ttu-id="80f3a-182">Om **alla** pingar till ett angivet mål inte fungerar `$False` returneras.</span><span class="sxs-lookup"><span data-stu-id="80f3a-182">If **all** pings to a given target fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="80f3a-183">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="80f3a-183">-ResolveDestination</span></span>

<span data-ttu-id="80f3a-184">Gör att cmdleten försöker matcha målets DNS-namn.</span><span class="sxs-lookup"><span data-stu-id="80f3a-184">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span> <span data-ttu-id="80f3a-185">När det används tillsammans med **traceroute** -parametern, kommer DNS-namnen för alla mellanliggande värdar också att hämtas, om möjligt.</span><span class="sxs-lookup"><span data-stu-id="80f3a-185">When used in conjunction with the **Traceroute** parameter, the DNS names of all intermediate hosts will also be retrieved, if possible.</span></span>

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

### <span data-ttu-id="80f3a-186">-Source</span><span class="sxs-lookup"><span data-stu-id="80f3a-186">-Source</span></span>

<span data-ttu-id="80f3a-187">Anger namnen på de datorer där pingen kommer.</span><span class="sxs-lookup"><span data-stu-id="80f3a-187">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="80f3a-188">Ange en kommaavgränsad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="80f3a-188">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="80f3a-189">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="80f3a-189">The default is the local computer.</span></span>

<span data-ttu-id="80f3a-190">**Obs:** Den här parametern fungerar inte i PowerShell-versionerna 6 och uppåt.</span><span class="sxs-lookup"><span data-stu-id="80f3a-190">**NOTE:** This parameter is not functional in PowerShell versions 6 and up.</span></span>
<span data-ttu-id="80f3a-191">Om du anger den här parametern påverkas inte kommandot.</span><span class="sxs-lookup"><span data-stu-id="80f3a-191">Supplying this parameter will have no effect on the command.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultPing, RepeatPing, TraceRoute, TcpPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-192">-TargetName</span><span class="sxs-lookup"><span data-stu-id="80f3a-192">-TargetName</span></span>

<span data-ttu-id="80f3a-193">Anger vilken eller vilka datorer som ska testas.</span><span class="sxs-lookup"><span data-stu-id="80f3a-193">Specifies the computer(s) to test.</span></span> <span data-ttu-id="80f3a-194">Ange dator namnen eller ange IP-adresser i IPv4-eller IPv6-format.</span><span class="sxs-lookup"><span data-stu-id="80f3a-194">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ComputerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-195">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="80f3a-195">-TimeoutSeconds</span></span>

<span data-ttu-id="80f3a-196">Anger timeout-värdet för testet.</span><span class="sxs-lookup"><span data-stu-id="80f3a-196">Sets the timeout value for the test.</span></span> <span data-ttu-id="80f3a-197">Testet Miss lyckas om ett svar inte tas emot innan tids gränsen upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="80f3a-197">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="80f3a-198">Standardvärdet är fem sekunder.</span><span class="sxs-lookup"><span data-stu-id="80f3a-198">The default is five seconds.</span></span>

<span data-ttu-id="80f3a-199">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="80f3a-199">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5 seconds
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-200">– Traceroute</span><span class="sxs-lookup"><span data-stu-id="80f3a-200">-Traceroute</span></span>

<span data-ttu-id="80f3a-201">Gör att cmdleten gör ett traceroute-test.</span><span class="sxs-lookup"><span data-stu-id="80f3a-201">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="80f3a-202">När den här parametern används returnerar cmdleten ett- `TestConnectionCommand+TraceStatus` objekt.</span><span class="sxs-lookup"><span data-stu-id="80f3a-202">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceStatus` object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TraceRoute
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-203">-MtuSize</span><span class="sxs-lookup"><span data-stu-id="80f3a-203">-MtuSize</span></span>

<span data-ttu-id="80f3a-204">Den här parametern används för att identifiera MTU-storleken för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="80f3a-204">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="80f3a-205">Cmdleten returnerar ett **PingReply # MTUSize** -objekt som innehåller sökvägen till MÅLETs MTU-storlek.</span><span class="sxs-lookup"><span data-stu-id="80f3a-205">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="80f3a-206">Mer information om MTU för sökvägen finns i artikeln [sökväg för MTU-identifiering](https://wikipedia.org/wiki/Path_MTU_Discovery) i wikipedia.</span><span class="sxs-lookup"><span data-stu-id="80f3a-206">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MtuSizeDetect
Aliases: MtuSizeDetect

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-207">– TcpPort</span><span class="sxs-lookup"><span data-stu-id="80f3a-207">-TcpPort</span></span>

<span data-ttu-id="80f3a-208">Anger TCP-portnumret på det mål som ska användas vid testet av TCP-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="80f3a-208">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="80f3a-209">Cmdleten kommer att försöka upprätta en TCP-anslutning till den angivna porten på målet.</span><span class="sxs-lookup"><span data-stu-id="80f3a-209">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

<span data-ttu-id="80f3a-210">Om en anslutning kan upprättas `$True` returneras.</span><span class="sxs-lookup"><span data-stu-id="80f3a-210">If a connection can be made, `$True` will be returned.</span></span>

<span data-ttu-id="80f3a-211">Om det inte går att upprätta en anslutning `$False` returneras.</span><span class="sxs-lookup"><span data-stu-id="80f3a-211">If a connection cannot be made, `$False` will be returned.</span></span>

```yaml
Type: System.Int32
Parameter Sets: TcpPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80f3a-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="80f3a-212">CommonParameters</span></span>

<span data-ttu-id="80f3a-213">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="80f3a-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="80f3a-214">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="80f3a-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="80f3a-215">INDATA</span><span class="sxs-lookup"><span data-stu-id="80f3a-215">INPUTS</span></span>

### <span data-ttu-id="80f3a-216">Inget</span><span class="sxs-lookup"><span data-stu-id="80f3a-216">None</span></span>

<span data-ttu-id="80f3a-217">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80f3a-217">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="80f3a-218">UTDATA</span><span class="sxs-lookup"><span data-stu-id="80f3a-218">OUTPUTS</span></span>

### <span data-ttu-id="80f3a-219">TestConnectionCommand + PingStatus, TestConnectionCommand + TraceStatus, Boolean, TestConnectionCommand + PingMtuStatus</span><span class="sxs-lookup"><span data-stu-id="80f3a-219">TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus</span></span>

<span data-ttu-id="80f3a-220">Som standard `Test-Connection` returnerar ett **TestConnectionCommand + PingStatus** -objekt för varje ping-svar.</span><span class="sxs-lookup"><span data-stu-id="80f3a-220">By default, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object for each ping reply.</span></span>

<span data-ttu-id="80f3a-221">Om du anger parametern **traceroute** returnerar cmdleten ett **TestConnectionCommand + TraceStatus** -objekt för varje ping-svar längs vägen.</span><span class="sxs-lookup"><span data-stu-id="80f3a-221">If you specify the **Traceroute** parameter, the cmdlet will return a **TestConnectionCommand+TraceStatus** object for each ping reply along the route.</span></span>

<span data-ttu-id="80f3a-222">Om du anger parametrarna **quiet** eller **TcpPort** returneras ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="80f3a-222">If you specify the **Quiet** or **TcpPort** parameters, it returns a **Boolean** value.</span></span> <span data-ttu-id="80f3a-223">Om flera anslutningar testas returneras en matris med **booleska** värden.</span><span class="sxs-lookup"><span data-stu-id="80f3a-223">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="80f3a-224">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="80f3a-224">NOTES</span></span>

## <span data-ttu-id="80f3a-225">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="80f3a-225">RELATED LINKS</span></span>

[<span data-ttu-id="80f3a-226">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="80f3a-226">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="80f3a-227">Stoppa – dator</span><span class="sxs-lookup"><span data-stu-id="80f3a-227">Stop-Computer</span></span>](Stop-Computer.md)
