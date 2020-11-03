---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 54ba1d7db60db7b4bb64f3161bba9c1fba124219
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263738"
---
# <span data-ttu-id="c166e-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="c166e-103">Test-Connection</span></span>

## <span data-ttu-id="c166e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c166e-104">SYNOPSIS</span></span>
<span data-ttu-id="c166e-105">Skickar ICMP Echo Request-paket, eller pingar, till en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="c166e-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="c166e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c166e-106">SYNTAX</span></span>

### <span data-ttu-id="c166e-107">PingCount (standard)</span><span class="sxs-lookup"><span data-stu-id="c166e-107">PingCount (Default)</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="c166e-108">PingContinues</span><span class="sxs-lookup"><span data-stu-id="c166e-108">PingContinues</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="c166e-109">DetectionOfMTUSize</span><span class="sxs-lookup"><span data-stu-id="c166e-109">DetectionOfMTUSize</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="c166e-110">TraceRoute</span><span class="sxs-lookup"><span data-stu-id="c166e-110">TraceRoute</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="c166e-111">ConnectionByTCPPort</span><span class="sxs-lookup"><span data-stu-id="c166e-111">ConnectionByTCPPort</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="c166e-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c166e-112">DESCRIPTION</span></span>

<span data-ttu-id="c166e-113">`Test-Connection`Cmdleten skickar Internet Control Message Protocol (ICMP) eko begär paket, eller pingar, till en eller flera fjärrdatorer och returnerar svars Svaren för eko.</span><span class="sxs-lookup"><span data-stu-id="c166e-113">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="c166e-114">Du kan använda den här cmdleten för att avgöra om en viss dator kan kontaktas i ett IP-nätverk.</span><span class="sxs-lookup"><span data-stu-id="c166e-114">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="c166e-115">Du kan använda parametrarna för `Test-Connection` för att ange både sändnings-och mottagnings datorer, köra kommandot som ett bakgrunds jobb för att ange ett timeout-värde och antalet pingar och för att konfigurera anslutningen och autentiseringen.</span><span class="sxs-lookup"><span data-stu-id="c166e-115">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="c166e-116">Till skillnad från det välkända **ping** -kommandot `Test-Connection` returnerar ett **TestConnectionCommand + PingReport** -objekt som du kan undersöka i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c166e-116">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingReport** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="c166e-117">Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt för varje testad anslutning.</span><span class="sxs-lookup"><span data-stu-id="c166e-117">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="c166e-118">Om flera anslutningar testas returneras en matris med **booleska** värden.</span><span class="sxs-lookup"><span data-stu-id="c166e-118">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="c166e-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c166e-119">EXAMPLES</span></span>

### <span data-ttu-id="c166e-120">Exempel 1: skicka eko förfrågningar till en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="c166e-120">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="c166e-121">Det här exemplet skickar eko begär ande paket från den lokala datorn till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c166e-121">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
Pinging Server01 [10.59.137.44] with 32 bytes of data:
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Ping complete.

Source     Destination Replies
------     ----------- -------
Server01   Server01    {System.Net.NetworkInformation.PingReply, System.Net.NetworkInformation ...
```

<span data-ttu-id="c166e-122">`Test-Connection` använder parametern **TargetName** för att ange Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c166e-122">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="c166e-123">**IPv4** -parametern anger protokollet för testet.</span><span class="sxs-lookup"><span data-stu-id="c166e-123">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="c166e-124">Ping-utdata skickas till **informations** data strömmen medan **TestConnectionCommand + PingReport** -objektet skickas **till den** resulterande data strömmen.</span><span class="sxs-lookup"><span data-stu-id="c166e-124">The ping output is sent to the **Information** stream while the **TestConnectionCommand+PingReport** object sent to the **Success** stream.</span></span> <span data-ttu-id="c166e-125">Mer information om utdata strömmar finns [about_Redirection](../microsoft.powershell.core/about/about_redirection.md).</span><span class="sxs-lookup"><span data-stu-id="c166e-125">For more information about the output streams, see [about_Redirection](../microsoft.powershell.core/about/about_redirection.md).</span></span>

### <span data-ttu-id="c166e-126">Exempel 2: skicka eko förfrågningar till flera datorer</span><span class="sxs-lookup"><span data-stu-id="c166e-126">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="c166e-127">I det här exemplet skickas pingar från den lokala datorn till flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="c166e-127">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="c166e-128">Exempel 3: skicka eko förfrågningar från flera datorer till en dator</span><span class="sxs-lookup"><span data-stu-id="c166e-128">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="c166e-129">I det här exemplet skickas pingar från olika käll datorer till en enda fjärran sluten dator, Server01.</span><span class="sxs-lookup"><span data-stu-id="c166e-129">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

<span data-ttu-id="c166e-130">Använd det här kommando formatet för att testa svars tiden för anslutningar från flera punkter.</span><span class="sxs-lookup"><span data-stu-id="c166e-130">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="c166e-131">Exempel 4: Använd parametrar för att anpassa test kommandot</span><span class="sxs-lookup"><span data-stu-id="c166e-131">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="c166e-132">I det här exemplet används parametrarna för `Test-Connection` för att anpassa kommandot.</span><span class="sxs-lookup"><span data-stu-id="c166e-132">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="c166e-133">Den lokala datorn skickar ett ping-test till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="c166e-133">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="c166e-134">`Test-Connection` använder parametern **TargetName** för att ange Server01.</span><span class="sxs-lookup"><span data-stu-id="c166e-134">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="c166e-135">Parametern **Count** anger att tre pingar skickas till Server01-datorn med en **fördröjning** på 2 sekunders intervall.</span><span class="sxs-lookup"><span data-stu-id="c166e-135">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="c166e-136">Du kan använda dessa alternativ när ping-svaret förväntas ta längre tid än vanligt, antingen på grund av ett utökat antal hopp eller ett nätverks tillstånd med hög trafik.</span><span class="sxs-lookup"><span data-stu-id="c166e-136">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="c166e-137">Exempel 5: köra ett test som bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="c166e-137">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="c166e-138">Det här exemplet visar hur du kör ett `Test-Connection` kommando som ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="c166e-138">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

<span data-ttu-id="c166e-139">`Start-Job`Kommandot använder `Test-Connection` cmdleten för att pinga många datorer i ett företag.</span><span class="sxs-lookup"><span data-stu-id="c166e-139">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="c166e-140">Värdet för parametern **TargetName** är ett `Get-Content` kommando som läser en lista med dator namn från `Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="c166e-140">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="c166e-141">Kommandot använder `Start-Job` cmdleten för att köra kommandot som ett bakgrunds jobb och det sparar jobbet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c166e-141">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="c166e-142">`if`Kommandot kontrollerar att jobbet fortfarande inte körs.</span><span class="sxs-lookup"><span data-stu-id="c166e-142">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="c166e-143">Om jobbet inte körs `Receive-Job` hämtar resultatet och lagrar dem i `$Results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c166e-143">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="c166e-144">Exempel 6: skapa endast en session om ett anslutnings test lyckas</span><span class="sxs-lookup"><span data-stu-id="c166e-144">Example 6: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="c166e-145">I det här exemplet skapas en session på Server01-datorn endast om minst en av pingarna som skickats till datorn lyckas.</span><span class="sxs-lookup"><span data-stu-id="c166e-145">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="c166e-146">`if`Kommandot använder `Test-Connection` cmdleten för att pinga Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c166e-146">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="c166e-147">Kommandot använder parametern **quiet** , som returnerar ett **booleskt** värde, i stället för ett **TestConnectionCommand + PingReport** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c166e-147">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **TestConnectionCommand+PingReport** object.</span></span>

<span data-ttu-id="c166e-148">Värdet är `$True` om någon av de fyra pingarna lyckas.</span><span class="sxs-lookup"><span data-stu-id="c166e-148">The value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="c166e-149">Om inget av pingarna lyckas är värdet `$False` .</span><span class="sxs-lookup"><span data-stu-id="c166e-149">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="c166e-150">Om `Test-Connection` kommandot returnerar ett värde av `$True` använder kommandot `New-PSSession` cmdleten för att skapa **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c166e-150">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span>

### <span data-ttu-id="c166e-151">Exempel 7: Använd parametern traceroute</span><span class="sxs-lookup"><span data-stu-id="c166e-151">Example 7: Use the Traceroute parameter</span></span>

<span data-ttu-id="c166e-152">Från och med PowerShell 6,0 mappar **traceroute** -parametern en väg mellan den lokala datorn och fjärrmålet som du anger med parametern **TargetName** .</span><span class="sxs-lookup"><span data-stu-id="c166e-152">Beginning in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

```powershell
Test-Connection -TargetName www.microsoft.com -Traceroute | ForEach-Object {
  $_ | Format-Table Source, DestinationAddress, DestinationHost
  $_.Replies | ForEach-Object {
      $_ | Format-Table Hop, ReplyRouterAddress
      $_.PingReplies | Format-Table
  }
}
```

```Output
Tracing route to www.microsoft.com [96.6.27.90] over a maximum of 128 hops:
  1   0 ms   0 ms   0 ms   192.168.0.3 [192.168.0.3]
  2   0 ms   0 ms   0 ms   192.168.1.1 [192.168.1.1]
  3   3 ms   29 ms   4 ms   96.6.27.90 [96.6.27.90]
Trace complete.

Source      DestinationAddress DestinationHost   Replies
------      ------------------ ---------------   -------
SERVER01    96.6.27.90         www.microsoft.com {, , }

Hop ReplyRouterAddress
--- ------------------
  1 192.168.0.3

    Status Address      RoundtripTime Options Buffer
    ------ -------      ------------- ------- ------
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  2 192.168.1.1

    Status Address     RoundtripTime Options Buffer
    ------ -------     ------------- ------- ------
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  3 96.6.27.90

 Status Address    RoundtripTime Options                                   Buffer
 ------ -------    ------------- -------                                   ------
Success 96.6.27.90             3 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             2 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             4 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
```

<span data-ttu-id="c166e-153">`Test-Connection`Kommandot använder parametern **traceroute** .</span><span class="sxs-lookup"><span data-stu-id="c166e-153">The `Test-Connection` command uses the **Traceroute** parameter.</span></span> <span data-ttu-id="c166e-154">Resultaten, som är `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objekt, är skickas till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c166e-154">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objects, are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="c166e-155">`ForEach-Object` skapar ett strukturerat utdata från de inneslutna `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objekten och efterföljande `[System.Net.NetworkInformation.PingReply]` objekt.</span><span class="sxs-lookup"><span data-stu-id="c166e-155">`ForEach-Object` creates a structured output of the contained `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objects and subsequent `[System.Net.NetworkInformation.PingReply]` objects.</span></span>

## <span data-ttu-id="c166e-156">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c166e-156">PARAMETERS</span></span>

### <span data-ttu-id="c166e-157">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="c166e-157">-BufferSize</span></span>

<span data-ttu-id="c166e-158">Anger storlek, i byte, för den buffert som skickas med det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="c166e-158">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="c166e-159">Standardvärdet är 32.</span><span class="sxs-lookup"><span data-stu-id="c166e-159">The default value is 32.</span></span>

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-160">-Antal</span><span class="sxs-lookup"><span data-stu-id="c166e-160">-Count</span></span>

<span data-ttu-id="c166e-161">Anger hur många eko-begäranden som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="c166e-161">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="c166e-162">Standardvärdet är 4.</span><span class="sxs-lookup"><span data-stu-id="c166e-162">The default value is 4.</span></span>

```yaml
Type: System.Int32
Parameter Sets: PingCount
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-163">-Fördröjning</span><span class="sxs-lookup"><span data-stu-id="c166e-163">-Delay</span></span>

<span data-ttu-id="c166e-164">Anger intervallet mellan pingar, i sekunder.</span><span class="sxs-lookup"><span data-stu-id="c166e-164">Specifies the interval between pings, in seconds.</span></span>

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-165">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="c166e-165">-DontFragment</span></span>

<span data-ttu-id="c166e-166">Den här parametern anger flaggan **Fragmentera inte** i IP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="c166e-166">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="c166e-167">Du kan använda den här parametern med parametern **BufferSize** för att testa MTU-storleken för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c166e-167">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="c166e-168">Mer information om MTU för sökvägen finns i artikeln [sökväg för MTU-identifiering](https://wikipedia.org/wiki/Path_MTU_Discovery) i wikipedia.</span><span class="sxs-lookup"><span data-stu-id="c166e-168">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-169">– IPv4</span><span class="sxs-lookup"><span data-stu-id="c166e-169">-IPv4</span></span>

<span data-ttu-id="c166e-170">Tvingar cmdleten att använda IPv4-protokollet för testet.</span><span class="sxs-lookup"><span data-stu-id="c166e-170">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="c166e-171">-IPv6</span><span class="sxs-lookup"><span data-stu-id="c166e-171">-IPv6</span></span>

<span data-ttu-id="c166e-172">Tvingar cmdleten att använda IPv6-protokollet för testet.</span><span class="sxs-lookup"><span data-stu-id="c166e-172">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="c166e-173">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="c166e-173">-MaxHops</span></span>

<span data-ttu-id="c166e-174">Anger maximalt antal hopp som ett meddelande om ICMP-begäran kan skickas.</span><span class="sxs-lookup"><span data-stu-id="c166e-174">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="c166e-175">Standardvärdet styrs av operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="c166e-175">The default value is controlled by the operating system.</span></span> <span data-ttu-id="c166e-176">Standardvärdet för Windows 10 är 128 hopp.</span><span class="sxs-lookup"><span data-stu-id="c166e-176">The default value for Windows 10 is 128 hops.</span></span>

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-177">-Ping</span><span class="sxs-lookup"><span data-stu-id="c166e-177">-Ping</span></span>

<span data-ttu-id="c166e-178">Gör att cmdleten gör ett ping-test, vilket är standard åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c166e-178">Causes the cmdlet to do a ping test, which is the default action.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: Ping test
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-179">– Tyst</span><span class="sxs-lookup"><span data-stu-id="c166e-179">-Quiet</span></span>

<span data-ttu-id="c166e-180">Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c166e-180">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="c166e-181">Om du använder den här parametern utelämnas alla fel.</span><span class="sxs-lookup"><span data-stu-id="c166e-181">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="c166e-182">Varje anslutning som testas returnerar ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="c166e-182">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="c166e-183">Om parametern **TargetName** anger flera datorer returneras en matris med **booleska** värden.</span><span class="sxs-lookup"><span data-stu-id="c166e-183">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="c166e-184">Om **några** pingar lyckas `$True` returneras.</span><span class="sxs-lookup"><span data-stu-id="c166e-184">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="c166e-185">Om **alla** pingar inte fungerar `$False` returneras.</span><span class="sxs-lookup"><span data-stu-id="c166e-185">If **all** pings fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="c166e-186">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="c166e-186">-ResolveDestination</span></span>

<span data-ttu-id="c166e-187">Gör att cmdleten försöker matcha målets DNS-namn.</span><span class="sxs-lookup"><span data-stu-id="c166e-187">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span>

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

### <span data-ttu-id="c166e-188">-Source</span><span class="sxs-lookup"><span data-stu-id="c166e-188">-Source</span></span>

<span data-ttu-id="c166e-189">Anger namnen på de datorer där pingen kommer.</span><span class="sxs-lookup"><span data-stu-id="c166e-189">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="c166e-190">Ange en kommaavgränsad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="c166e-190">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="c166e-191">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c166e-191">The default is the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: PingCount, PingContinues, TraceRoute, ConnectionByTCPPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-192">-TargetName</span><span class="sxs-lookup"><span data-stu-id="c166e-192">-TargetName</span></span>

<span data-ttu-id="c166e-193">Anger vilka datorer som ska testas.</span><span class="sxs-lookup"><span data-stu-id="c166e-193">Specifies the computers to test.</span></span> <span data-ttu-id="c166e-194">Ange dator namnen eller ange IP-adresser i IPv4-eller IPv6-format.</span><span class="sxs-lookup"><span data-stu-id="c166e-194">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="c166e-195">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c166e-195">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="c166e-196">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="c166e-196">This parameter is required.</span></span> <span data-ttu-id="c166e-197">**Computername** är ett alias för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="c166e-197">**ComputerName** is an alias for this parameter.</span></span>

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

### <span data-ttu-id="c166e-198">– TCPPort</span><span class="sxs-lookup"><span data-stu-id="c166e-198">-TCPPort</span></span>

<span data-ttu-id="c166e-199">Anger TCP-portnumret på det mål som ska användas vid testet av TCP-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="c166e-199">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="c166e-200">Cmdleten kommer att försöka upprätta en TCP-anslutning till den angivna porten på målet.</span><span class="sxs-lookup"><span data-stu-id="c166e-200">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ConnectionByTCPPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-201">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="c166e-201">-TimeoutSeconds</span></span>

<span data-ttu-id="c166e-202">Anger timeout-värdet för testet.</span><span class="sxs-lookup"><span data-stu-id="c166e-202">Sets the timeout value for the test.</span></span> <span data-ttu-id="c166e-203">Testet Miss lyckas om ett svar inte tas emot innan tids gränsen upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="c166e-203">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="c166e-204">Standardvärdet är fem sekunder.</span><span class="sxs-lookup"><span data-stu-id="c166e-204">The default is five seconds.</span></span>

<span data-ttu-id="c166e-205">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="c166e-205">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="c166e-206">– Traceroute</span><span class="sxs-lookup"><span data-stu-id="c166e-206">-Traceroute</span></span>

<span data-ttu-id="c166e-207">Gör att cmdleten gör ett traceroute-test.</span><span class="sxs-lookup"><span data-stu-id="c166e-207">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="c166e-208">När den här parametern används returnerar cmdleten ett- `TestConnectionCommand+TraceRouteResult` objekt.</span><span class="sxs-lookup"><span data-stu-id="c166e-208">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceRouteResult` object.</span></span>

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

### <span data-ttu-id="c166e-209">– Fortsätter</span><span class="sxs-lookup"><span data-stu-id="c166e-209">-Continues</span></span>

<span data-ttu-id="c166e-210">Gör att cmdleten skickar ping-begäranden kontinuerligt.</span><span class="sxs-lookup"><span data-stu-id="c166e-210">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="c166e-211">Den här parametern kan inte användas med **Count** -parametern.</span><span class="sxs-lookup"><span data-stu-id="c166e-211">This parameter can't be used with the **Count** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingContinues
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-212">-MTUSizeDetect</span><span class="sxs-lookup"><span data-stu-id="c166e-212">-MTUSizeDetect</span></span>

<span data-ttu-id="c166e-213">Den här parametern används för att identifiera MTU-storleken för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c166e-213">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="c166e-214">Cmdleten returnerar ett **PingReply # MTUSize** -objekt som innehåller sökvägen till MÅLETs MTU-storlek.</span><span class="sxs-lookup"><span data-stu-id="c166e-214">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="c166e-215">Mer information om MTU för sökvägen finns i artikeln [sökväg för MTU-identifiering](https://wikipedia.org/wiki/Path_MTU_Discovery) i wikipedia.</span><span class="sxs-lookup"><span data-stu-id="c166e-215">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetectionOfMTUSize
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c166e-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c166e-216">CommonParameters</span></span>

<span data-ttu-id="c166e-217">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c166e-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c166e-218">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c166e-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c166e-219">INDATA</span><span class="sxs-lookup"><span data-stu-id="c166e-219">INPUTS</span></span>

### <span data-ttu-id="c166e-220">Inget</span><span class="sxs-lookup"><span data-stu-id="c166e-220">None</span></span>

<span data-ttu-id="c166e-221">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c166e-221">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c166e-222">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c166e-222">OUTPUTS</span></span>

### <span data-ttu-id="c166e-223">TestConnectionCommand + PingReport, TestConnectionCommand + TraceRouteResult, Boolean, PingReply # MTUSize</span><span class="sxs-lookup"><span data-stu-id="c166e-223">TestConnectionCommand+PingReport, TestConnectionCommand+TraceRouteResult, Boolean, PingReply#MTUSize</span></span>

<span data-ttu-id="c166e-224">Om du anger en **quiet** -parameter returneras ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="c166e-224">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="c166e-225">Om flera anslutningar testas returneras en matris med **booleska** värden.</span><span class="sxs-lookup"><span data-stu-id="c166e-225">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="c166e-226">Annars `Test-Connection` returnerar ett **TestConnectionCommand + PingReport** -objekt för varje ping.</span><span class="sxs-lookup"><span data-stu-id="c166e-226">Otherwise, `Test-Connection` returns a **TestConnectionCommand+PingReport** object for each ping.</span></span>

## <span data-ttu-id="c166e-227">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c166e-227">NOTES</span></span>

## <span data-ttu-id="c166e-228">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c166e-228">RELATED LINKS</span></span>

[<span data-ttu-id="c166e-229">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="c166e-229">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="c166e-230">Stoppa – dator</span><span class="sxs-lookup"><span data-stu-id="c166e-230">Stop-Computer</span></span>](Stop-Computer.md)
