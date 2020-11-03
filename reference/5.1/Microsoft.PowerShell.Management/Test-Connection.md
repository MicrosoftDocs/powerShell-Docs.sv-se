---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: a8d3923db69a20cfada58391944b592cf999e6ef
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265317"
---
# <span data-ttu-id="dd7aa-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="dd7aa-103">Test-Connection</span></span>

## <span data-ttu-id="dd7aa-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dd7aa-104">SYNOPSIS</span></span>
<span data-ttu-id="dd7aa-105">Skickar ICMP Echo Request-paket, eller pingar, till en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="dd7aa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dd7aa-106">SYNTAX</span></span>

### <span data-ttu-id="dd7aa-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="dd7aa-107">Default (Default)</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="dd7aa-108">Källa</span><span class="sxs-lookup"><span data-stu-id="dd7aa-108">Source</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="dd7aa-109">Tyst</span><span class="sxs-lookup"><span data-stu-id="dd7aa-109">Quiet</span></span>

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## <span data-ttu-id="dd7aa-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dd7aa-110">DESCRIPTION</span></span>

<span data-ttu-id="dd7aa-111">`Test-Connection`Cmdleten skickar Internet Control Message Protocol (ICMP) eko begär paket, eller pingar, till en eller flera fjärrdatorer och returnerar svars Svaren för eko.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-111">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="dd7aa-112">Du kan använda den här cmdleten för att avgöra om en viss dator kan kontaktas i ett IP-nätverk.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-112">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="dd7aa-113">Du kan använda parametrarna för `Test-Connection` för att ange både sändnings-och mottagnings datorer, köra kommandot som ett bakgrunds jobb för att ange ett timeout-värde och antalet pingar och för att konfigurera anslutningen och autentiseringen.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-113">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="dd7aa-114">Till skillnad från det välkända **ping** -kommandot `Test-Connection` returnerar ett **Win32_PingStatus** -objekt som du kan undersöka i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-114">Unlike the familiar **ping** command, `Test-Connection` returns a **Win32_PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="dd7aa-115">Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt för varje testad anslutning.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-115">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="dd7aa-116">Om flera anslutningar testas returneras en matris med **booleska** värden.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-116">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="dd7aa-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dd7aa-117">EXAMPLES</span></span>

### <span data-ttu-id="dd7aa-118">Exempel 1: skicka eko förfrågningar till en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="dd7aa-118">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="dd7aa-119">Det här exemplet skickar eko begär ande paket från den lokala datorn till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-119">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

```powershell
Test-Connection -ComputerName Server01
```

```Output
Source        Destination     IPV4Address     IPV6Address  Bytes    Time(ms)
------        -----------     -----------     -----------  -----    --------
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       1
```

<span data-ttu-id="dd7aa-120">`Test-Connection` använder parametern **computername** för att ange Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-120">`Test-Connection` uses the **ComputerName** parameter to specify the Server01 computer.</span></span>

### <span data-ttu-id="dd7aa-121">Exempel 2: skicka eko förfrågningar till flera datorer</span><span class="sxs-lookup"><span data-stu-id="dd7aa-121">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="dd7aa-122">I det här exemplet skickas pingar från den lokala datorn till flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-122">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### <span data-ttu-id="dd7aa-123">Exempel 3: skicka eko förfrågningar från flera datorer till en dator</span><span class="sxs-lookup"><span data-stu-id="dd7aa-123">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="dd7aa-124">I det här exemplet skickas pingar från olika käll datorer till en enda fjärran sluten dator, Server01.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-124">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="dd7aa-125">`Test-Connection` använder parametern **Credential** för att ange autentiseringsuppgifterna för en användare som har behörighet att skicka en ping-begäran från käll datorerna.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-125">`Test-Connection` uses the **Credential** parameter to specify the credentials of a user who has permission to send a ping request from the source computers.</span></span> <span data-ttu-id="dd7aa-126">Använd det här kommando formatet för att testa svars tiden för anslutningar från flera punkter.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-126">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="dd7aa-127">Exempel 4: Använd parametrar för att anpassa test kommandot</span><span class="sxs-lookup"><span data-stu-id="dd7aa-127">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="dd7aa-128">I det här exemplet används parametrarna för `Test-Connection` för att anpassa kommandot.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-128">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="dd7aa-129">Den lokala datorn skickar ett ping-test till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-129">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

<span data-ttu-id="dd7aa-130">`Test-Connection` använder parametern **computername** för att ange Server01.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-130">`Test-Connection` uses the **ComputerName** parameter to specify Server01.</span></span> <span data-ttu-id="dd7aa-131">Parametern **Count** anger att tre pingar skickas till Server01-datorn med en **fördröjning** på 2 sekunders intervall.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-131">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="dd7aa-132">Du kan använda dessa alternativ när ping-svaret förväntas ta längre tid än vanligt, antingen på grund av ett utökat antal hopp eller ett nätverks tillstånd med hög trafik.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-132">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="dd7aa-133">Exempel 5: köra ett test som bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="dd7aa-133">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="dd7aa-134">Det här exemplet visar hur du kör ett `Test-Connection` kommando som ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-134">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

<span data-ttu-id="dd7aa-135">`Test-Connection`Kommandot pingar många datorer i ett företag.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-135">The `Test-Connection` command pings many computers in an enterprise.</span></span> <span data-ttu-id="dd7aa-136">Värdet för parametern **computername** är ett `Get-Content` kommando som läser en lista med dator namn från `Servers.txt file` .</span><span class="sxs-lookup"><span data-stu-id="dd7aa-136">The value of the **ComputerName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt file`.</span></span> <span data-ttu-id="dd7aa-137">Kommandot använder parametern **AsJob** för att köra kommandot som ett bakgrunds jobb och det sparar jobbet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-137">The command uses the **AsJob** parameter to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="dd7aa-138">`if`Kommandot kontrollerar att jobbet fortfarande inte körs.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-138">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="dd7aa-139">Om jobbet inte körs `Receive-Job` hämtar resultatet och lagrar dem i `$Results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-139">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="dd7aa-140">Exempel 6: pinga en fjärrdator med autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="dd7aa-140">Example 6: Ping a remote computer with credentials</span></span>

<span data-ttu-id="dd7aa-141">Det här kommandot använder `Test-Connection` cmdleten för att pinga en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-141">This command uses the `Test-Connection` cmdlet to ping a remote computer.</span></span>

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

<span data-ttu-id="dd7aa-142">Kommandot använder parametern **Credential** för att ange ett användar konto som har behörighet att pinga fjärrdatorn och **personifieringstoken** -parametern för att ändra personifieringsnivån som ska **identifieras**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-142">The command uses the **Credential** parameter to specify a user account that has permission to ping the remote computer and the **Impersonation** parameter to change the impersonation level to **Identify**.</span></span>

### <span data-ttu-id="dd7aa-143">Exempel 7: skapa en session endast om ett anslutnings test lyckas</span><span class="sxs-lookup"><span data-stu-id="dd7aa-143">Example 7: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="dd7aa-144">I det här exemplet skapas en session på Server01-datorn endast om minst en av pingarna som skickats till datorn lyckas.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-144">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="dd7aa-145">`if`Kommandot använder `Test-Connection` cmdleten för att pinga Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-145">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="dd7aa-146">Kommandot använder parametern **quiet** , som returnerar ett **booleskt** värde, i stället för ett **Win32_PingStatus** -objekt.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-146">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **Win32_PingStatus** object.</span></span> <span data-ttu-id="dd7aa-147">Värdet är `$True` om någon av de fyra pingarna lyckas och är, i annat fall, `$False` .</span><span class="sxs-lookup"><span data-stu-id="dd7aa-147">The value is `$True` if any of the four pings succeed and is, otherwise, `$False`.</span></span>

<span data-ttu-id="dd7aa-148">Om `Test-Connection` kommandot returnerar ett värde av `$True` använder kommandot `New-PSSession` cmdleten för att skapa **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-148">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span>

## <span data-ttu-id="dd7aa-149">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dd7aa-149">PARAMETERS</span></span>

### <span data-ttu-id="dd7aa-150">– AsJob</span><span class="sxs-lookup"><span data-stu-id="dd7aa-150">-AsJob</span></span>

<span data-ttu-id="dd7aa-151">Anger att denna cmdlet körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-151">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="dd7aa-152">Om du vill använda den här parametern måste lokal och fjärran sluten dator konfigureras för fjärr kommunikation och, i Windows Vista och senare versioner av Windows-operativsystemet, måste du öppna PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="dd7aa-152">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="dd7aa-153">Mer information finns i [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd7aa-153">For more information, see [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="dd7aa-154">När du anger parametern **AsJob** returnerar kommandot omedelbart ett objekt som representerar bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-154">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="dd7aa-155">Du kan fortsätta att arbeta i sessionen medan jobbet är klart.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-155">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="dd7aa-156">Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-156">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="dd7aa-157">Använd cmdleten för att hämta jobb resultatet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="dd7aa-157">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="dd7aa-158">Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md).</span><span class="sxs-lookup"><span data-stu-id="dd7aa-158">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-159">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="dd7aa-159">-BufferSize</span></span>

<span data-ttu-id="dd7aa-160">Anger storlek, i byte, för den buffert som skickas med det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-160">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="dd7aa-161">Standardvärdet är 32.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-161">The default value is 32.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="dd7aa-162">-ComputerName</span></span>

<span data-ttu-id="dd7aa-163">Anger vilka datorer som pingas.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-163">Specifies the computers to ping.</span></span> <span data-ttu-id="dd7aa-164">Ange dator namnen eller ange IP-adresser i IPv4-eller IPv6-format.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-164">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="dd7aa-165">Jokertecken tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-165">Wildcard characters are not permitted.</span></span> <span data-ttu-id="dd7aa-166">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-166">This parameter is required.</span></span>

<span data-ttu-id="dd7aa-167">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-167">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="dd7aa-168">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-168">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

> [!NOTE]
> <span data-ttu-id="dd7aa-169">Parametern **computername** byter namn till **TargetName** i PowerShell 6,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-169">The **ComputerName** parameter is renamed to **TargetName** in PowerShell 6.0 and above.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, IPAddress, __SERVER, Server, Destination

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-170">-Antal</span><span class="sxs-lookup"><span data-stu-id="dd7aa-170">-Count</span></span>

<span data-ttu-id="dd7aa-171">Anger hur många eko-begäranden som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-171">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="dd7aa-172">Standardvärdet är 4.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-172">The default value is 4.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="dd7aa-173">-Credential</span></span>

<span data-ttu-id="dd7aa-174">Anger ett användar konto som har behörighet att skicka en ping-begäran från käll datorn.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-174">Specifies a user account that has permission to send a ping request from the source computer.</span></span> <span data-ttu-id="dd7aa-175">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett från `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-175">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="dd7aa-176">Parametern **Credential** är bara giltig när **käll** parametern används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-176">The **Credential** parameter is valid only when the **Source** parameter is used in the command.</span></span> <span data-ttu-id="dd7aa-177">Autentiseringsuppgifterna påverkar inte mål datorn.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-177">The credentials don't affect the destination computer.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Source
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-178">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="dd7aa-178">-DcomAuthentication</span></span>

<span data-ttu-id="dd7aa-179">Anger den autentiseringsnivå som denna cmdlet använder med WMI.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-179">Specifies the authentication level that this cmdlet uses with WMI.</span></span>
<span data-ttu-id="dd7aa-180">`Test-Connection` använder WMI.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-180">`Test-Connection` uses WMI.</span></span>
<span data-ttu-id="dd7aa-181">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="dd7aa-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dd7aa-182">**Standard**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-182">**Default**.</span></span> <span data-ttu-id="dd7aa-183">Windows-autentisering</span><span class="sxs-lookup"><span data-stu-id="dd7aa-183">Windows Authentication</span></span>
- <span data-ttu-id="dd7aa-184">**Ingen**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-184">**None**.</span></span> <span data-ttu-id="dd7aa-185">Ingen COM-autentisering</span><span class="sxs-lookup"><span data-stu-id="dd7aa-185">No COM authentication</span></span>
- <span data-ttu-id="dd7aa-186">**Anslut**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-186">**Connect**.</span></span> <span data-ttu-id="dd7aa-187">COM-autentisering på anslutnings nivå</span><span class="sxs-lookup"><span data-stu-id="dd7aa-187">Connect-level COM authentication</span></span>
- <span data-ttu-id="dd7aa-188">**Anropa**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-188">**Call**.</span></span> <span data-ttu-id="dd7aa-189">COM-autentisering på anrops nivå</span><span class="sxs-lookup"><span data-stu-id="dd7aa-189">Call-level COM authentication</span></span>
- <span data-ttu-id="dd7aa-190">**Paket**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-190">**Packet**.</span></span> <span data-ttu-id="dd7aa-191">COM-autentisering på paket nivå</span><span class="sxs-lookup"><span data-stu-id="dd7aa-191">Packet-level COM authentication</span></span>
- <span data-ttu-id="dd7aa-192">**PacketIntegrity**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-192">**PacketIntegrity**.</span></span> <span data-ttu-id="dd7aa-193">COM-autentisering på paket integritets nivå</span><span class="sxs-lookup"><span data-stu-id="dd7aa-193">Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="dd7aa-194">**PacketPrivacy**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-194">**PacketPrivacy**.</span></span> <span data-ttu-id="dd7aa-195">COM-autentisering för paket sekretess nivå</span><span class="sxs-lookup"><span data-stu-id="dd7aa-195">Packet Privacy-level COM authentication</span></span>
- <span data-ttu-id="dd7aa-196">**Oförändrad**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-196">**Unchanged**.</span></span> <span data-ttu-id="dd7aa-197">Samma som föregående kommando</span><span class="sxs-lookup"><span data-stu-id="dd7aa-197">Same as the previous command</span></span>

<span data-ttu-id="dd7aa-198">Standardvärdet är **paket** som har ett uppräknat värde på **4**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-198">The default value is **Packet** that has an enumerated value of **4**.</span></span> <span data-ttu-id="dd7aa-199">Mer information om värdena för den här parametern finns i [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) -uppräkning.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-199">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) enumeration.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet (enumerated value of 4)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-200">-Fördröjning</span><span class="sxs-lookup"><span data-stu-id="dd7aa-200">-Delay</span></span>

<span data-ttu-id="dd7aa-201">Anger intervallet mellan pingar, i sekunder.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-201">Specifies the interval between pings, in seconds.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1 (second)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-202">-Personifiering</span><span class="sxs-lookup"><span data-stu-id="dd7aa-202">-Impersonation</span></span>

<span data-ttu-id="dd7aa-203">Anger personifieringsnivån som ska användas när den här cmdleten anropar WMI.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-203">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="dd7aa-204">`Test-Connection` använder WMI.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-204">`Test-Connection` uses WMI.</span></span>

<span data-ttu-id="dd7aa-205">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="dd7aa-205">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="dd7aa-206">**Standard**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-206">**Default**.</span></span> <span data-ttu-id="dd7aa-207">Standard personifiering.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-207">Default impersonation.</span></span>
- <span data-ttu-id="dd7aa-208">**Anonym**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-208">**Anonymous**.</span></span> <span data-ttu-id="dd7aa-209">Döljer anroparens identitet.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-209">Hides the identity of the caller.</span></span>
- <span data-ttu-id="dd7aa-210">**Identifiera**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-210">**Identify**.</span></span> <span data-ttu-id="dd7aa-211">Tillåter att objekt frågar efter anroparens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-211">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="dd7aa-212">**Personifiera**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-212">**Impersonate**.</span></span> <span data-ttu-id="dd7aa-213">Tillåter att objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-213">Allows objects to use the credentials of the caller.</span></span>

<span data-ttu-id="dd7aa-214">Standardvärdet är **personifierat**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-214">The default value is **Impersonate**.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-215">-Protocol</span><span class="sxs-lookup"><span data-stu-id="dd7aa-215">-Protocol</span></span>

<span data-ttu-id="dd7aa-216">Anger ett protokoll.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-216">Specifies a protocol.</span></span> <span data-ttu-id="dd7aa-217">De acceptabla värdena för den här parametern är DCOM och WSMan.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-217">The acceptable values for this parameter are DCOM and WSMan.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-218">– Tyst</span><span class="sxs-lookup"><span data-stu-id="dd7aa-218">-Quiet</span></span>

<span data-ttu-id="dd7aa-219">Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-219">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="dd7aa-220">Om du använder den här parametern utelämnas alla fel.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-220">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="dd7aa-221">Varje anslutning som testas returnerar ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-221">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="dd7aa-222">Om parametern **computername** anger flera datorer returneras en matris med **booleska** värden.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-222">If the **ComputerName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="dd7aa-223">Om **några** pingar lyckas `$True` returneras.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-223">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="dd7aa-224">Om **alla** pingar inte fungerar `$False` returneras.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-224">If **all** pings fail, `$False` is returned.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Quiet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-225">-Source</span><span class="sxs-lookup"><span data-stu-id="dd7aa-225">-Source</span></span>

<span data-ttu-id="dd7aa-226">Anger namnen på de datorer där pingen kommer.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-226">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="dd7aa-227">Ange en kommaavgränsad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-227">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="dd7aa-228">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-228">The default is the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: FCN, SRC

Required: True
Position: 1
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-229">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="dd7aa-229">-ThrottleLimit</span></span>

<span data-ttu-id="dd7aa-230">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-230">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="dd7aa-231">Om du utelämnar den här parametern eller anger värdet 0, används standardvärdet 32.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-231">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="dd7aa-232">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-232">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-233">– TimeToLive</span><span class="sxs-lookup"><span data-stu-id="dd7aa-233">-TimeToLive</span></span>

<span data-ttu-id="dd7aa-234">Anger det maximala antal gånger som ett paket kan vidarebefordras.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-234">Specifies the maximum times a packet can be forwarded.</span></span> <span data-ttu-id="dd7aa-235">För varje hopp i Gateway, routrar osv. **TimeToLive** -värdet minskas med ett.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-235">For every hop in gateways, routers etc. the **TimeToLive** value is decreased by one.</span></span> <span data-ttu-id="dd7aa-236">Vid noll ignoreras paketet och ett fel returneras.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-236">At zero the packet is discarded and an error is returned.</span></span>
<span data-ttu-id="dd7aa-237">I **Windows** är standardvärdet **128**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-237">In **Windows** , The default value is **128**.</span></span> <span data-ttu-id="dd7aa-238">Aliaset för parametern **TimeToLive** är **TTL**.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-238">The alias of the **TimeToLive** parameter is **TTL**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TTL

Required: False
Position: Named
Default value: 128 in Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-239">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="dd7aa-239">-WsmanAuthentication</span></span>

<span data-ttu-id="dd7aa-240">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-240">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span>
<span data-ttu-id="dd7aa-241">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="dd7aa-241">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dd7aa-242">Basic</span><span class="sxs-lookup"><span data-stu-id="dd7aa-242">Basic</span></span>
- <span data-ttu-id="dd7aa-243">CredSSP</span><span class="sxs-lookup"><span data-stu-id="dd7aa-243">CredSSP</span></span>
- <span data-ttu-id="dd7aa-244">Default</span><span class="sxs-lookup"><span data-stu-id="dd7aa-244">Default</span></span>
- <span data-ttu-id="dd7aa-245">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="dd7aa-245">Digest</span></span>
- <span data-ttu-id="dd7aa-246">Kerberos</span><span class="sxs-lookup"><span data-stu-id="dd7aa-246">Kerberos</span></span>
- <span data-ttu-id="dd7aa-247">Fram.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-247">Negotiate.</span></span>

<span data-ttu-id="dd7aa-248">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-248">The default value is Default.</span></span>

<span data-ttu-id="dd7aa-249">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="dd7aa-249">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0).</span></span>

<span data-ttu-id="dd7aa-250">Varning! autentisering med Credential Security Service Provider (CredSSP), där autentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-250">Caution: Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="dd7aa-251">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-251">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="dd7aa-252">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-252">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="dd7aa-253">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dd7aa-254">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dd7aa-254">CommonParameters</span></span>

<span data-ttu-id="dd7aa-255">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-255">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dd7aa-256">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dd7aa-256">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dd7aa-257">INDATA</span><span class="sxs-lookup"><span data-stu-id="dd7aa-257">INPUTS</span></span>

### <span data-ttu-id="dd7aa-258">Inget</span><span class="sxs-lookup"><span data-stu-id="dd7aa-258">None</span></span>

<span data-ttu-id="dd7aa-259">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-259">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="dd7aa-260">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dd7aa-260">OUTPUTS</span></span>

### <span data-ttu-id="dd7aa-261">System. Management. ManagementObject # root\cimv2\ Win32_PingStatus, system. Management. Automation. RemotingJob, system. Boolean</span><span class="sxs-lookup"><span data-stu-id="dd7aa-261">System.Management.ManagementObject#root\cimv2\Win32_PingStatus, System.Management.Automation.RemotingJob, System.Boolean</span></span>

<span data-ttu-id="dd7aa-262">Den här cmdleten returnerar ett jobb objekt, om du anger parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="dd7aa-262">This cmdlet returns a job object, if you specify the **AsJob** parameter.</span></span>

<span data-ttu-id="dd7aa-263">Om du anger en **quiet** -parameter returneras ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-263">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="dd7aa-264">Om flera anslutningar testas returneras en matris med **booleska** värden.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-264">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="dd7aa-265">Annars `Test-Connection` returneras ett **Win32_PingStatus** -objekt för varje ping.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-265">Otherwise, `Test-Connection` returns a **Win32_PingStatus** object for each ping.</span></span>

## <span data-ttu-id="dd7aa-266">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dd7aa-266">NOTES</span></span>

<span data-ttu-id="dd7aa-267">Denna cmdlet använder klassen **Win32_PingStatus** .</span><span class="sxs-lookup"><span data-stu-id="dd7aa-267">This cmdlet uses the **Win32_PingStatus** class.</span></span> <span data-ttu-id="dd7aa-268">Ett `Get-WMIObject Win32_PingStatus` kommando motsvarar ett `Test-Connection` kommando.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-268">A `Get-WMIObject Win32_PingStatus` command is equivalent to a `Test-Connection` command.</span></span>

<span data-ttu-id="dd7aa-269">**Käll** parameter uppsättningen introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dd7aa-269">The **Source** parameter set was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="dd7aa-270">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dd7aa-270">RELATED LINKS</span></span>

[<span data-ttu-id="dd7aa-271">Lägg till dator</span><span class="sxs-lookup"><span data-stu-id="dd7aa-271">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="dd7aa-272">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="dd7aa-272">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="dd7aa-273">Stoppa – dator</span><span class="sxs-lookup"><span data-stu-id="dd7aa-273">Stop-Computer</span></span>](Stop-Computer.md)
