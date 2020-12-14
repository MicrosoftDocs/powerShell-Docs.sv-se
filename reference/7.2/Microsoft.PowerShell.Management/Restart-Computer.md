---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 0e6df859a19f2281cc835b725fbc52c232042e56
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709924"
---
# <span data-ttu-id="fe569-102">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="fe569-102">Restart-Computer</span></span>

## <span data-ttu-id="fe569-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fe569-103">SYNOPSIS</span></span>
<span data-ttu-id="fe569-104">Startar om operativ systemet på lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="fe569-104">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="fe569-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fe569-105">SYNTAX</span></span>

### <span data-ttu-id="fe569-106">DefaultSet (standard)</span><span class="sxs-lookup"><span data-stu-id="fe569-106">DefaultSet (Default)</span></span>

```
Restart-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential]<PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fe569-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fe569-107">DESCRIPTION</span></span>

<span data-ttu-id="fe569-108">`Restart-Computer`Cmdleten startar om operativ systemet på lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="fe569-108">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="fe569-109">Du kan använda parametrarna för `Restart-Computer` för att köra omstarts åtgärderna för att ange autentiseringsnivåer och alternativa autentiseringsuppgifter, för att begränsa de åtgärder som körs samtidigt, och framtvinga en omedelbar omstart.</span><span class="sxs-lookup"><span data-stu-id="fe569-109">You can use the parameters of `Restart-Computer` to run the restart operations, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="fe569-110">Från och med Windows PowerShell 3,0 kan du vänta på att omstarten ska slutföras innan du kör nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="fe569-110">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="fe569-111">Ange ett timeout-värde och frågeintervall för väntan och vänta tills vissa tjänster är tillgängliga på den omstartade datorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-111">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="fe569-112">Den här funktionen gör det praktiskt att använda `Restart-Computer` i skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="fe569-112">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

## <span data-ttu-id="fe569-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fe569-113">EXAMPLES</span></span>

### <span data-ttu-id="fe569-114">Exempel 1: starta om den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="fe569-114">Example 1: Restart the local computer</span></span>

<span data-ttu-id="fe569-115">`Restart-Computer` startar om den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-115">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="fe569-116">Exempel 2: starta om flera datorer</span><span class="sxs-lookup"><span data-stu-id="fe569-116">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="fe569-117">`Restart-Computer` kan starta om fjärrdatorer och lokala datorer.</span><span class="sxs-lookup"><span data-stu-id="fe569-117">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="fe569-118">Parametern **computername** accepterar en matris med dator namn.</span><span class="sxs-lookup"><span data-stu-id="fe569-118">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="fe569-119">Exempel 3: Hämta dator namn från en textfil</span><span class="sxs-lookup"><span data-stu-id="fe569-119">Example 3: Get computer names from a text file</span></span>

<span data-ttu-id="fe569-120">`Restart-Computer` hämtar en lista med dator namn från en textfil och startar om datorerna.</span><span class="sxs-lookup"><span data-stu-id="fe569-120">`Restart-Computer` gets a list of computer names from a text file and restarts the computers.</span></span> <span data-ttu-id="fe569-121">Parametern **computername** har inte angetts.</span><span class="sxs-lookup"><span data-stu-id="fe569-121">The **ComputerName** parameter isn't specified.</span></span> <span data-ttu-id="fe569-122">Men eftersom det är den första positions parametern, accepterar den dator namnen från text filen som skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="fe569-122">But because it's the first position parameter, it accepts the computer names from the text file that are sent down the pipeline.</span></span>

```powershell
Get-Content -Path C:\Domain01.txt | Restart-Computer
```

<span data-ttu-id="fe569-123">`Get-Content` använder parametern **Path** för att hämta en lista över dator namn från en textfil **Domain01.txt**.</span><span class="sxs-lookup"><span data-stu-id="fe569-123">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="fe569-124">Dator namnen skickas ned i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="fe569-124">The computer names are sent down the pipeline.</span></span> <span data-ttu-id="fe569-125">`Restart-Computer` startar om varje dator.</span><span class="sxs-lookup"><span data-stu-id="fe569-125">`Restart-Computer` restarts each computer.</span></span>

### <span data-ttu-id="fe569-126">Exempel 4: Framtvinga omstart av datorer som anges i en textfil</span><span class="sxs-lookup"><span data-stu-id="fe569-126">Example 4: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="fe569-127">Det här exemplet tvingar fram en omedelbar omstart av de datorer som anges i `Domain01.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="fe569-127">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="fe569-128">Dator namnen från text filen lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="fe569-128">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="fe569-129">**Force** -parametern tvingar en omedelbar omstart.</span><span class="sxs-lookup"><span data-stu-id="fe569-129">The **Force** parameter forces an immediate restart.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force
```

<span data-ttu-id="fe569-130">`Get-Content` använder parametern **Path** för att hämta en lista över dator namn från en textfil **Domain01.txt**.</span><span class="sxs-lookup"><span data-stu-id="fe569-130">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="fe569-131">Dator namnen lagras i variabeln `$Names` .</span><span class="sxs-lookup"><span data-stu-id="fe569-131">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="fe569-132">`Get-Credential` du uppmanas att ange ett användar namn och lösen ord och lagrar värdena i variabeln `$Creds` .</span><span class="sxs-lookup"><span data-stu-id="fe569-132">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="fe569-133">`Restart-Computer` använder parametrarna **computername** och **Credential** med deras variabler.</span><span class="sxs-lookup"><span data-stu-id="fe569-133">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="fe569-134">**Force** -parametern orsakar en omedelbar omstart av varje dator.</span><span class="sxs-lookup"><span data-stu-id="fe569-134">The **Force** parameter causes an immediate restart of each computer.</span></span>

### <span data-ttu-id="fe569-135">Exempel 6: starta om en fjärrdator och vänta på PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe569-135">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="fe569-136">`Restart-Computer` startar om fjärrdatorn och väntar sedan upp till 5 minuter (300 sekunder) för att PowerShell ska bli tillgängligt på den omstartade datorn innan den fortsätter.</span><span class="sxs-lookup"><span data-stu-id="fe569-136">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="fe569-137">`Restart-Computer` använder parametern **computername** för att ange **Server01**.</span><span class="sxs-lookup"><span data-stu-id="fe569-137">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="fe569-138">Parametern **wait** väntar på att omstarten ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="fe569-138">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="fe569-139">**For** anger att PowerShell kan köra kommandon på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-139">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="fe569-140">Parametern **timeout** anger en vänte tid på fem minuter.</span><span class="sxs-lookup"><span data-stu-id="fe569-140">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="fe569-141">Parametern **Delay** frågar den fjärranslutna datorn varannan sekund för att avgöra om den startas om.</span><span class="sxs-lookup"><span data-stu-id="fe569-141">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="fe569-142">Exempel 7: starta om en dator med hjälp av WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="fe569-142">Example 7: Restart a computer by using WsmanAuthentication</span></span>

<span data-ttu-id="fe569-143">`Restart-Computer` startar om fjärrdatorn med **WsmanAuthentication** -mekanismen.</span><span class="sxs-lookup"><span data-stu-id="fe569-143">`Restart-Computer` restarts the remote computer using the **WsmanAuthentication** mechanism.</span></span>
<span data-ttu-id="fe569-144">Kerberos-autentisering avgör om den aktuella användaren har behörighet att starta om fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-144">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span> <span data-ttu-id="fe569-145">Mer information finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="fe569-145">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```powershell
Restart-Computer -ComputerName Server01 -WsmanAuthentication Kerberos
```

<span data-ttu-id="fe569-146">`Restart-Computer` använder parametern **computername** för att ange fjärrdatorn **Server01**.</span><span class="sxs-lookup"><span data-stu-id="fe569-146">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01**.</span></span>
<span data-ttu-id="fe569-147">Parametern **WsmanAuthentication** anger autentiseringsmetoden som **Kerberos**.</span><span class="sxs-lookup"><span data-stu-id="fe569-147">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos**.</span></span>

## <span data-ttu-id="fe569-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fe569-148">PARAMETERS</span></span>

### <span data-ttu-id="fe569-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="fe569-149">-ComputerName</span></span>

<span data-ttu-id="fe569-150">Anger ett dator namn eller en kommaavgränsad matris med dator namn.</span><span class="sxs-lookup"><span data-stu-id="fe569-150">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="fe569-151">`Restart-Computer` accepterar **computername** -objekt från pipelinen eller variablerna.</span><span class="sxs-lookup"><span data-stu-id="fe569-151">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="fe569-152">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="fe569-152">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="fe569-153">Om du vill ange den lokala datorn skriver du datorns namn, en punkt `.` eller localhost.</span><span class="sxs-lookup"><span data-stu-id="fe569-153">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="fe569-154">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="fe569-154">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="fe569-155">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="fe569-155">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="fe569-156">Om parametern **computername** inte anges startar om `Restart-Computer` den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-156">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fe569-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="fe569-157">-Credential</span></span>

<span data-ttu-id="fe569-158">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fe569-158">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="fe569-159">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="fe569-159">The default is the current user.</span></span>

<span data-ttu-id="fe569-160">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fe569-160">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="fe569-161">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="fe569-161">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="fe569-162">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="fe569-162">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="fe569-163">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="fe569-163">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe569-164">-Fördröjning</span><span class="sxs-lookup"><span data-stu-id="fe569-164">-Delay</span></span>

<span data-ttu-id="fe569-165">Anger frekvensen för frågor, i sekunder.</span><span class="sxs-lookup"><span data-stu-id="fe569-165">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="fe569-166">PowerShell frågar tjänsten som anges av **for** -parametern för att avgöra om tjänsten är tillgänglig efter att datorn startats om.</span><span class="sxs-lookup"><span data-stu-id="fe569-166">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="fe569-167">Den här parametern är endast giltig tillsammans med parametrarna **wait** och **for** .</span><span class="sxs-lookup"><span data-stu-id="fe569-167">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="fe569-168">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fe569-168">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="fe569-169">Om **förskjutnings** parametern inte anges, `Restart-Computer` använder en fördröjning på fem sekunder.</span><span class="sxs-lookup"><span data-stu-id="fe569-169">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe569-170">– För</span><span class="sxs-lookup"><span data-stu-id="fe569-170">-For</span></span>

<span data-ttu-id="fe569-171">Anger PowerShell-beteendet som väntar på att den angivna tjänsten eller funktionen ska bli tillgänglig när datorn har startats om.</span><span class="sxs-lookup"><span data-stu-id="fe569-171">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="fe569-172">Den här parametern är endast giltig med parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="fe569-172">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="fe569-173">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="fe569-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fe569-174">**Standard**: väntar på att PowerShell ska starta om.</span><span class="sxs-lookup"><span data-stu-id="fe569-174">**Default**: Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="fe569-175">**PowerShell**: kan köra kommandon i en PowerShell-fjärrsession på datorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-175">**PowerShell**: Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="fe569-176">**WMI**: tar emot ett svar på en Win32_ComputerSystem fråga för datorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-176">**WMI**: Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="fe569-177">**WinRM**: kan upprätta en fjärrsession till datorn med hjälp av WS-Management.</span><span class="sxs-lookup"><span data-stu-id="fe569-177">**WinRM**: Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="fe569-178">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fe569-178">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: (All)
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe569-179">-Force</span><span class="sxs-lookup"><span data-stu-id="fe569-179">-Force</span></span>

<span data-ttu-id="fe569-180">Tvingar en omedelbar omstart av datorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-180">Forces an immediate restart of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe569-181">-Timeout</span><span class="sxs-lookup"><span data-stu-id="fe569-181">-Timeout</span></span>

<span data-ttu-id="fe569-182">Anger vänte tiden i sekunder för vänte tiden.</span><span class="sxs-lookup"><span data-stu-id="fe569-182">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="fe569-183">När tids gränsen har gått `Restart-Computer` tillbaka återgår till kommando tolken även om datorerna inte startas om.</span><span class="sxs-lookup"><span data-stu-id="fe569-183">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="fe569-184">Parametern **timeout** är bara giltig med parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="fe569-184">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="fe569-185">**Tids gränsen** åsidosätter **wait** -parameterns obestämda vänte tid.</span><span class="sxs-lookup"><span data-stu-id="fe569-185">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="fe569-186">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fe569-186">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe569-187">– Vänta</span><span class="sxs-lookup"><span data-stu-id="fe569-187">-Wait</span></span>

<span data-ttu-id="fe569-188">`Restart-Computer` ignorerar PowerShell-prompten och blockerar pipelinen tills datorerna har startats om.</span><span class="sxs-lookup"><span data-stu-id="fe569-188">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="fe569-189">Du kan använda den här parametern i ett skript för att starta om datorer och sedan fortsätta att bearbeta när omstarten är färdig.</span><span class="sxs-lookup"><span data-stu-id="fe569-189">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="fe569-190">Parametern **wait** väntar på obestämd tid för datorerna som ska startas om.</span><span class="sxs-lookup"><span data-stu-id="fe569-190">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="fe569-191">Du kan använda **timeout** för att justera tiden och parametrarna **for** och **Delay** för att vänta tills vissa tjänster blir tillgängliga på de omstartade datorerna.</span><span class="sxs-lookup"><span data-stu-id="fe569-191">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="fe569-192">Parametern **wait** är inte giltig när du startar om den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-192">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="fe569-193">Om värdet för parametern **computername** innehåller namnen på fjärrdatorer och den lokala datorn `Restart-Computer` genererar ett icke-avslutande fel som **väntar** på den lokala datorn, men väntar på att fjärrdatorerna ska starta om.</span><span class="sxs-lookup"><span data-stu-id="fe569-193">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="fe569-194">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fe569-194">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="fe569-195">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="fe569-195">-WsmanAuthentication</span></span>

<span data-ttu-id="fe569-196">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="fe569-196">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="fe569-197">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fe569-197">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="fe569-198">De acceptabla värdena för den här parametern är: **Basic**, **CredSSP**, **default**, **Digest**, **Kerberos** och **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="fe569-198">The acceptable values for this parameter are: **Basic**, **CredSSP**, **Default**, **Digest**, **Kerberos**, and **Negotiate**.</span></span>

<span data-ttu-id="fe569-199">Mer information finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="fe569-199">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="fe569-200">Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="fe569-200">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="fe569-201">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="fe569-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="fe569-202">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe569-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe569-203">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fe569-203">-Confirm</span></span>

<span data-ttu-id="fe569-204">Du uppmanas att bekräfta innan du kör `Restart-Computer` .</span><span class="sxs-lookup"><span data-stu-id="fe569-204">Prompts you for confirmation before running `Restart-Computer`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe569-205">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fe569-205">-WhatIf</span></span>

<span data-ttu-id="fe569-206">Visar vad som händer om `Restart-Computer` körningarna körs.</span><span class="sxs-lookup"><span data-stu-id="fe569-206">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="fe569-207">`Restart-Computer`Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="fe569-207">The `Restart-Computer` cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe569-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fe569-208">CommonParameters</span></span>

<span data-ttu-id="fe569-209">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fe569-209">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fe569-210">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fe569-210">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fe569-211">INDATA</span><span class="sxs-lookup"><span data-stu-id="fe569-211">INPUTS</span></span>

### <span data-ttu-id="fe569-212">System. String</span><span class="sxs-lookup"><span data-stu-id="fe569-212">System.String</span></span>

<span data-ttu-id="fe569-213">`Restart-Computer` accepterar dator namn från pipelinen eller variablerna.</span><span class="sxs-lookup"><span data-stu-id="fe569-213">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

## <span data-ttu-id="fe569-214">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fe569-214">OUTPUTS</span></span>

### <span data-ttu-id="fe569-215">Inga</span><span class="sxs-lookup"><span data-stu-id="fe569-215">None</span></span>

<span data-ttu-id="fe569-216">`Restart-Computer` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="fe569-216">`Restart-Computer` doesn't generate any output.</span></span>

## <span data-ttu-id="fe569-217">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fe569-217">NOTES</span></span>

- <span data-ttu-id="fe569-218">I Windows `Restart-Computer` använder Win32Shutdown- [metoden](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) i [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) -klassen Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="fe569-218">In Windows, `Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span> <span data-ttu-id="fe569-219">Den här metoden kräver att **SeShutdownPrivilege** -behörighet aktive ras för det användar konto som används för att starta om datorn.</span><span class="sxs-lookup"><span data-stu-id="fe569-219">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>
- <span data-ttu-id="fe569-220">På Linux och Mac OS `Restart-Computer` använder `/sbin/shutdown` verktyget bash.</span><span class="sxs-lookup"><span data-stu-id="fe569-220">On Linux and Mac OS, `Restart-Computer` uses the `/sbin/shutdown` bash tool.</span></span>

## <span data-ttu-id="fe569-221">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fe569-221">RELATED LINKS</span></span>

[<span data-ttu-id="fe569-222">Om Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="fe569-222">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="fe569-223">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="fe569-223">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="fe569-224">WS-Managementprotokollet</span><span class="sxs-lookup"><span data-stu-id="fe569-224">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
