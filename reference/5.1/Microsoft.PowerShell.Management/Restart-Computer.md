---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 553b61c9669afab325e9feec101d701c2b9a7c83
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268233"
---
# <span data-ttu-id="c4635-103">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="c4635-103">Restart-Computer</span></span>

## <span data-ttu-id="c4635-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c4635-104">SYNOPSIS</span></span>
<span data-ttu-id="c4635-105">Startar om operativ systemet på lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="c4635-105">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="c4635-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c4635-106">SYNTAX</span></span>

### <span data-ttu-id="c4635-107">DefaultSet (standard)</span><span class="sxs-lookup"><span data-stu-id="c4635-107">DefaultSet (Default)</span></span>

```
Restart-Computer [-DcomAuthentication <AuthenticationLevel>] [-Impersonation <ImpersonationLevel>]
 [-WsmanAuthentication <String>] [-Protocol <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c4635-108">AsJobSet</span><span class="sxs-lookup"><span data-stu-id="c4635-108">AsJobSet</span></span>

```
Restart-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>]
 [-Impersonation <ImpersonationLevel>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Force] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c4635-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c4635-109">DESCRIPTION</span></span>

<span data-ttu-id="c4635-110">`Restart-Computer`Cmdleten startar om operativ systemet på lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="c4635-110">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="c4635-111">Du kan använda parametrarna för `Restart-Computer` för att köra omstarts åtgärderna som ett bakgrunds jobb, för att ange autentiseringsnivåer och alternativa autentiseringsuppgifter, för att begränsa de åtgärder som körs samtidigt, och framtvinga en omedelbar omstart.</span><span class="sxs-lookup"><span data-stu-id="c4635-111">You can use the parameters of `Restart-Computer` to run the restart operations as a background job, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="c4635-112">Från och med Windows PowerShell 3,0 kan du vänta på att omstarten ska slutföras innan du kör nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="c4635-112">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="c4635-113">Ange ett timeout-värde och frågeintervall för väntan och vänta tills vissa tjänster är tillgängliga på den omstartade datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-113">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="c4635-114">Den här funktionen gör det praktiskt att använda `Restart-Computer` i skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="c4635-114">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

<span data-ttu-id="c4635-115">Du kan använda WS-Management-protokollet (WSMan) för att starta om datorn, om DCOM-anrop (Distributed Component Object Model) blockeras, till exempel av en Enterprise-brandvägg.</span><span class="sxs-lookup"><span data-stu-id="c4635-115">You can use the WS-Management (WSMan) protocol to restart the computer, in case Distributed Component Object Model (DCOM) calls are blocked, such as by an enterprise firewall.</span></span> <span data-ttu-id="c4635-116">Mer information finns i [WS-Management-protokollet](/windows/desktop/WinRM/ws-management-protocol).</span><span class="sxs-lookup"><span data-stu-id="c4635-116">For more information, see [WS-Management Protocol](/windows/desktop/WinRM/ws-management-protocol).</span></span>

<span data-ttu-id="c4635-117">Denna cmdlet kräver Windows PowerShell-fjärrkommunikation endast när du använder parametern **AsJob** i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="c4635-117">This cmdlet requires Windows PowerShell remoting only when you use the **AsJob** parameter in a command.</span></span>

## <span data-ttu-id="c4635-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c4635-118">EXAMPLES</span></span>

### <span data-ttu-id="c4635-119">Exempel 1: starta om den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="c4635-119">Example 1: Restart the local computer</span></span>

<span data-ttu-id="c4635-120">`Restart-Computer` startar om den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-120">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="c4635-121">Exempel 2: starta om flera datorer</span><span class="sxs-lookup"><span data-stu-id="c4635-121">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="c4635-122">`Restart-Computer` kan starta om fjärrdatorer och lokala datorer.</span><span class="sxs-lookup"><span data-stu-id="c4635-122">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="c4635-123">Parametern **computername** accepterar en matris med dator namn.</span><span class="sxs-lookup"><span data-stu-id="c4635-123">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="c4635-124">Exempel 3: starta om datorer som ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="c4635-124">Example 3: Restart computers as a background job</span></span>

<span data-ttu-id="c4635-125">Kommandona kör ett `Restart-Computer` kommando som bakgrunds jobb på två fjärrdatorer och hämtar sedan resultaten.</span><span class="sxs-lookup"><span data-stu-id="c4635-125">These commands run a `Restart-Computer` command as a background job on two remote computers, and then get the results.</span></span>

<span data-ttu-id="c4635-126">Eftersom **AsJob** skapar jobbet på den lokala datorn och automatiskt returnerar resultaten till den lokala datorn, kan du köra `Receive-Job` som ett lokalt kommando.</span><span class="sxs-lookup"><span data-stu-id="c4635-126">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

```powershell
$Job = Restart-Computer -ComputerName "Server01", "Server02" -AsJob
$Job | Receive-Job
```

<span data-ttu-id="c4635-127">`Restart-Computer` använder parametern **computername** för att ange **Server01** och **Server02**.</span><span class="sxs-lookup"><span data-stu-id="c4635-127">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** and **Server02**.</span></span> <span data-ttu-id="c4635-128">Parametern **AsJob** kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="c4635-128">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="c4635-129">Jobbobjektet lagras i `$Job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c4635-129">The job object is stored in the `$Job` variable.</span></span> <span data-ttu-id="c4635-130">`$Job` skickas pipelinen till den `Receive-Job` cmdlet som hämtar resultatet.</span><span class="sxs-lookup"><span data-stu-id="c4635-130">`$Job` is sent down the pipeline to the `Receive-Job` cmdlet that gets the results.</span></span>

### <span data-ttu-id="c4635-131">Exempel 4: starta om en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="c4635-131">Example 4: Restart a remote computer</span></span>

<span data-ttu-id="c4635-132">`Restart-Computer` startar om en fjärrdator med anpassade inställningar för personifiering och autentisering.</span><span class="sxs-lookup"><span data-stu-id="c4635-132">`Restart-Computer` restarts a remote computer with customized impersonation and authentication settings.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="c4635-133">`Restart-Computer` använder parametern **computername** för att ange **Server01**.</span><span class="sxs-lookup"><span data-stu-id="c4635-133">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="c4635-134">**Personifiering** -parametern anger anonym för att dölja beställarens identitet.</span><span class="sxs-lookup"><span data-stu-id="c4635-134">The **Impersonation** parameter specifies Anonymous to hide the requester's identity.</span></span> <span data-ttu-id="c4635-135">Parametern **DcomAuthentication** anger PacketIntegrity som anslutningens autentiseringsnivå.</span><span class="sxs-lookup"><span data-stu-id="c4635-135">The **DcomAuthentication** parameter specifies PacketIntegrity as the connection's authentication level.</span></span>

### <span data-ttu-id="c4635-136">Exempel 5: Framtvinga omstart av datorer som anges i en textfil</span><span class="sxs-lookup"><span data-stu-id="c4635-136">Example 5: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="c4635-137">Det här exemplet tvingar fram en omedelbar omstart av de datorer som anges i `Domain01.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="c4635-137">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="c4635-138">Dator namnen från text filen lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="c4635-138">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="c4635-139">Force-parametern tvingar **fram** en omedelbar omstart och **ThrottleLimit** -parametern begränsar antalet samtidiga anslutningar.</span><span class="sxs-lookup"><span data-stu-id="c4635-139">The **Force** parameter forces an immediate restart and the **ThrottleLimit** parameter limits the number of concurrent connections.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force -ThrottleLimit 10
```

<span data-ttu-id="c4635-140">`Get-Content` använder parametern **Path** för att hämta en lista över dator namn från en textfil **Domain01.txt**.</span><span class="sxs-lookup"><span data-stu-id="c4635-140">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="c4635-141">Dator namnen lagras i variabeln `$Names` .</span><span class="sxs-lookup"><span data-stu-id="c4635-141">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="c4635-142">`Get-Credential` du uppmanas att ange ett användar namn och lösen ord och lagrar värdena i variabeln `$Creds` .</span><span class="sxs-lookup"><span data-stu-id="c4635-142">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="c4635-143">`Restart-Computer` använder parametrarna **computername** och **Credential** med deras variabler.</span><span class="sxs-lookup"><span data-stu-id="c4635-143">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="c4635-144">**Force** -parametern orsakar en omedelbar omstart av varje dator.</span><span class="sxs-lookup"><span data-stu-id="c4635-144">The **Force** parameter causes an immediate restart of each computer.</span></span> <span data-ttu-id="c4635-145">Parametern **ThrottleLimit** begränsar kommandot till 10 samtidiga anslutningar.</span><span class="sxs-lookup"><span data-stu-id="c4635-145">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span>

### <span data-ttu-id="c4635-146">Exempel 6: starta om en fjärrdator och vänta på PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4635-146">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="c4635-147">`Restart-Computer` startar om fjärrdatorn och väntar sedan upp till 5 minuter (300 sekunder) för att PowerShell ska bli tillgängligt på den omstartade datorn innan den fortsätter.</span><span class="sxs-lookup"><span data-stu-id="c4635-147">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="c4635-148">`Restart-Computer` använder parametern **computername** för att ange **Server01**.</span><span class="sxs-lookup"><span data-stu-id="c4635-148">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="c4635-149">Parametern **wait** väntar på att omstarten ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="c4635-149">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="c4635-150">**For** anger att PowerShell kan köra kommandon på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-150">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="c4635-151">Parametern **timeout** anger en vänte tid på fem minuter.</span><span class="sxs-lookup"><span data-stu-id="c4635-151">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="c4635-152">Parametern **Delay** frågar den fjärranslutna datorn varannan sekund för att avgöra om den startas om.</span><span class="sxs-lookup"><span data-stu-id="c4635-152">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="c4635-153">Exempel 7: starta om en dator med hjälp av WSMan-protokollet</span><span class="sxs-lookup"><span data-stu-id="c4635-153">Example 7: Restart a computer by using the WSMan Protocol</span></span>

<span data-ttu-id="c4635-154">`Restart-Computer` startar om fjärrdatorn med hjälp av WSMan-protokollet i stället för standard DCOM.</span><span class="sxs-lookup"><span data-stu-id="c4635-154">`Restart-Computer` restarts the remote computer by using the WSMan protocol instead of the default, DCOM.</span></span> <span data-ttu-id="c4635-155">Kerberos-autentisering avgör om den aktuella användaren har behörighet att starta om fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-155">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span>

<span data-ttu-id="c4635-156">De här inställningarna är utformade för företag där DCOM-baserade omstarter inte fungerar eftersom DCOM är blockerad.</span><span class="sxs-lookup"><span data-stu-id="c4635-156">These settings are designed for enterprises in which DCOM-based restarts fail because DCOM is blocked.</span></span> <span data-ttu-id="c4635-157">Till exempel av en brand vägg.</span><span class="sxs-lookup"><span data-stu-id="c4635-157">For example, by a firewall.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Protocol WSMan -WsmanAuthentication Kerberos
```

<span data-ttu-id="c4635-158">`Restart-Computer` använder parametern **computername** för att ange fjärrdatorn **Server01**.</span><span class="sxs-lookup"><span data-stu-id="c4635-158">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01**.</span></span>
<span data-ttu-id="c4635-159">**Protokoll** parametern anger att WSMan-protokollet ska användas.</span><span class="sxs-lookup"><span data-stu-id="c4635-159">The **Protocol** parameter specifies to use the WSMan protocol.</span></span> <span data-ttu-id="c4635-160">Parametern **WsmanAuthentication** anger autentiseringsmetoden som **Kerberos**.</span><span class="sxs-lookup"><span data-stu-id="c4635-160">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos**.</span></span>

## <span data-ttu-id="c4635-161">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c4635-161">PARAMETERS</span></span>

### <span data-ttu-id="c4635-162">– AsJob</span><span class="sxs-lookup"><span data-stu-id="c4635-162">-AsJob</span></span>

<span data-ttu-id="c4635-163">Anger att `Restart-Computer` körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="c4635-163">Indicates that `Restart-Computer` runs as a background job.</span></span>

<span data-ttu-id="c4635-164">Om du vill använda den här parametern måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="c4635-164">To use this parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="c4635-165">I Windows Vista och senare versioner av operativ systemet Windows måste du öppna PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="c4635-165">On Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as Administrator** option.</span></span> <span data-ttu-id="c4635-166">Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4635-166">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="c4635-167">När du anger parametern **AsJob** returnerar kommandot omedelbart ett objekt som representerar bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="c4635-167">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="c4635-168">Du kan fortsätta att arbeta i sessionen medan jobbet är klart.</span><span class="sxs-lookup"><span data-stu-id="c4635-168">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="c4635-169">Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-169">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="c4635-170">Använd **jobb** -cmdletar för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="c4635-170">To manage the job, use the **Job** cmdlets.</span></span> <span data-ttu-id="c4635-171">Använd cmdleten för att hämta jobb resultatet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="c4635-171">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="c4635-172">Mer information om bakgrunds jobb i Windows PowerShell finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="c4635-172">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-173">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c4635-173">-ComputerName</span></span>

<span data-ttu-id="c4635-174">Anger ett dator namn eller en kommaavgränsad matris med dator namn.</span><span class="sxs-lookup"><span data-stu-id="c4635-174">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="c4635-175">`Restart-Computer` accepterar **computername** -objekt från pipelinen eller variablerna.</span><span class="sxs-lookup"><span data-stu-id="c4635-175">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="c4635-176">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="c4635-176">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="c4635-177">Om du vill ange den lokala datorn skriver du datorns namn, en punkt `.` eller localhost.</span><span class="sxs-lookup"><span data-stu-id="c4635-177">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="c4635-178">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="c4635-178">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="c4635-179">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="c4635-179">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="c4635-180">Om parametern **computername** inte anges startar om `Restart-Computer` den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-180">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

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

### <span data-ttu-id="c4635-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="c4635-181">-Credential</span></span>

<span data-ttu-id="c4635-182">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c4635-182">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="c4635-183">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="c4635-183">The default is the current user.</span></span>

<span data-ttu-id="c4635-184">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c4635-184">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c4635-185">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="c4635-185">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="c4635-186">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="c4635-186">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="c4635-187">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="c4635-187">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="c4635-188">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="c4635-188">-DcomAuthentication</span></span>

<span data-ttu-id="c4635-189">Anger den autentiseringsnivå som används för WMI-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="c4635-189">Specifies the authentication level that is used for the WMI connection.</span></span> <span data-ttu-id="c4635-190">`Restart-Computer` använder WMI.</span><span class="sxs-lookup"><span data-stu-id="c4635-190">`Restart-Computer` uses WMI.</span></span>

<span data-ttu-id="c4635-191">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="c4635-191">Valid values are:</span></span>

- <span data-ttu-id="c4635-192">**Anropa** : com-autentisering på anrops nivå</span><span class="sxs-lookup"><span data-stu-id="c4635-192">**Call** :            Call-level COM authentication</span></span>
- <span data-ttu-id="c4635-193">**Anslut** : com-autentisering på anslutnings nivå</span><span class="sxs-lookup"><span data-stu-id="c4635-193">**Connect** :         Connect-level COM authentication</span></span>
- <span data-ttu-id="c4635-194">**Standard** : Windows-autentisering</span><span class="sxs-lookup"><span data-stu-id="c4635-194">**Default** :         Windows Authentication</span></span>
- <span data-ttu-id="c4635-195">**Ingen** : ingen com-autentisering</span><span class="sxs-lookup"><span data-stu-id="c4635-195">**None** :            No COM authentication</span></span>
- <span data-ttu-id="c4635-196">**Paket** : com-autentisering på paket nivå.</span><span class="sxs-lookup"><span data-stu-id="c4635-196">**Packet** :          Packet-level COM authentication.</span></span>
- <span data-ttu-id="c4635-197">**PacketIntegrity** : com-autentisering på paket integritets nivå</span><span class="sxs-lookup"><span data-stu-id="c4635-197">**PacketIntegrity** : Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="c4635-198">**PacketPrivacy** : com-autentisering på paket sekretess nivå.</span><span class="sxs-lookup"><span data-stu-id="c4635-198">**PacketPrivacy** :   Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="c4635-199">**Oförändrad** : autentiseringsnivån är samma som föregående kommando.</span><span class="sxs-lookup"><span data-stu-id="c4635-199">**Unchanged** :       The authentication level is the same as the previous command.</span></span>

<span data-ttu-id="c4635-200">Mer information finns i [AuthenticationLevel-uppräkning](/dotnet/api/system.management.authenticationlevel).</span><span class="sxs-lookup"><span data-stu-id="c4635-200">For more information, see [AuthenticationLevel Enumeration](/dotnet/api/system.management.authenticationlevel).</span></span>

<span data-ttu-id="c4635-201">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4635-201">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-202">-Fördröjning</span><span class="sxs-lookup"><span data-stu-id="c4635-202">-Delay</span></span>

<span data-ttu-id="c4635-203">Anger frekvensen för frågor, i sekunder.</span><span class="sxs-lookup"><span data-stu-id="c4635-203">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="c4635-204">PowerShell frågar tjänsten som anges av **for** -parametern för att avgöra om tjänsten är tillgänglig efter att datorn startats om.</span><span class="sxs-lookup"><span data-stu-id="c4635-204">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="c4635-205">Den här parametern är endast giltig tillsammans med parametrarna **wait** och **for** .</span><span class="sxs-lookup"><span data-stu-id="c4635-205">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="c4635-206">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4635-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="c4635-207">Om **förskjutnings** parametern inte anges, `Restart-Computer` använder en fördröjning på fem sekunder.</span><span class="sxs-lookup"><span data-stu-id="c4635-207">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-208">– För</span><span class="sxs-lookup"><span data-stu-id="c4635-208">-For</span></span>

<span data-ttu-id="c4635-209">Anger PowerShell-beteendet som väntar på att den angivna tjänsten eller funktionen ska bli tillgänglig när datorn har startats om.</span><span class="sxs-lookup"><span data-stu-id="c4635-209">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="c4635-210">Den här parametern är endast giltig med parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="c4635-210">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="c4635-211">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="c4635-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c4635-212">**Standard** : väntar på att PowerShell ska starta om.</span><span class="sxs-lookup"><span data-stu-id="c4635-212">**Default** : Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="c4635-213">**PowerShell** : kan köra kommandon i en PowerShell-fjärrsession på datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-213">**PowerShell** : Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="c4635-214">**WMI** : tar emot ett svar på en Win32_ComputerSystem fråga för datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-214">**WMI** : Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="c4635-215">**WinRM** : kan upprätta en fjärrsession till datorn med hjälp av WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c4635-215">**WinRM** : Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="c4635-216">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4635-216">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: DefaultSet
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-217">-Force</span><span class="sxs-lookup"><span data-stu-id="c4635-217">-Force</span></span>

<span data-ttu-id="c4635-218">Tvingar en omedelbar omstart av datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-218">Forces an immediate restart of the computer.</span></span>

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

### <span data-ttu-id="c4635-219">-Personifiering</span><span class="sxs-lookup"><span data-stu-id="c4635-219">-Impersonation</span></span>

<span data-ttu-id="c4635-220">Anger personifieringsnivån som denna cmdlet använder för att anropa WMI.</span><span class="sxs-lookup"><span data-stu-id="c4635-220">Specifies the impersonation level that this cmdlet uses to call WMI.</span></span> <span data-ttu-id="c4635-221">`Restart-Computer` använder WMI.</span><span class="sxs-lookup"><span data-stu-id="c4635-221">`Restart-Computer` uses WMI.</span></span>
<span data-ttu-id="c4635-222">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="c4635-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c4635-223">**Standard** : standard-personifiering.</span><span class="sxs-lookup"><span data-stu-id="c4635-223">**Default** : Default impersonation.</span></span> <span data-ttu-id="c4635-224">Trots namnet är detta inte standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="c4635-224">Despite the name, this isn't the default value.</span></span>
- <span data-ttu-id="c4635-225">**Anonym** : döljer anroparens identitet.</span><span class="sxs-lookup"><span data-stu-id="c4635-225">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="c4635-226">**Identifiera** : tillåter objekt att fråga om autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="c4635-226">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="c4635-227">**Personifiera** : tillåter att objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="c4635-227">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-228">-Protocol</span><span class="sxs-lookup"><span data-stu-id="c4635-228">-Protocol</span></span>

<span data-ttu-id="c4635-229">Anger vilket protokoll som ska användas för att starta om datorerna.</span><span class="sxs-lookup"><span data-stu-id="c4635-229">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="c4635-230">Giltiga värden är **WSMan** och **DCOM**.</span><span class="sxs-lookup"><span data-stu-id="c4635-230">The valid values are **WSMan** and **DCOM**.</span></span>

<span data-ttu-id="c4635-231">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4635-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-232">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c4635-232">-ThrottleLimit</span></span>

<span data-ttu-id="c4635-233">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="c4635-233">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="c4635-234">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-234">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="c4635-235">Om parametern **ThrottleLimit** inte anges eller värdet 0 används, `Restart-Computer` använder högst 32 samtidiga anslutningar.</span><span class="sxs-lookup"><span data-stu-id="c4635-235">If the **ThrottleLimit** parameter isn't specified or a value of 0 is used, `Restart-Computer` uses a maximum of 32 concurrent connections.</span></span>

```yaml
Type: System.Int32
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-236">-Timeout</span><span class="sxs-lookup"><span data-stu-id="c4635-236">-Timeout</span></span>

<span data-ttu-id="c4635-237">Anger vänte tiden i sekunder för vänte tiden.</span><span class="sxs-lookup"><span data-stu-id="c4635-237">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="c4635-238">När tids gränsen har gått `Restart-Computer` tillbaka återgår till kommando tolken även om datorerna inte startas om.</span><span class="sxs-lookup"><span data-stu-id="c4635-238">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="c4635-239">Parametern **timeout** är bara giltig med parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="c4635-239">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="c4635-240">**Tids gränsen** åsidosätter **wait** -parameterns obestämda vänte tid.</span><span class="sxs-lookup"><span data-stu-id="c4635-240">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="c4635-241">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4635-241">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultSet
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-242">– Vänta</span><span class="sxs-lookup"><span data-stu-id="c4635-242">-Wait</span></span>

<span data-ttu-id="c4635-243">`Restart-Computer` ignorerar PowerShell-prompten och blockerar pipelinen tills datorerna har startats om.</span><span class="sxs-lookup"><span data-stu-id="c4635-243">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="c4635-244">Du kan använda den här parametern i ett skript för att starta om datorer och sedan fortsätta att bearbeta när omstarten är färdig.</span><span class="sxs-lookup"><span data-stu-id="c4635-244">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="c4635-245">Parametern **wait** väntar på obestämd tid för datorerna som ska startas om.</span><span class="sxs-lookup"><span data-stu-id="c4635-245">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="c4635-246">Du kan använda **timeout** för att justera tiden och parametrarna **for** och **Delay** för att vänta tills vissa tjänster blir tillgängliga på de omstartade datorerna.</span><span class="sxs-lookup"><span data-stu-id="c4635-246">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="c4635-247">Parametern **wait** är inte giltig när du startar om den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-247">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="c4635-248">Om värdet för parametern **computername** innehåller namnen på fjärrdatorer och den lokala datorn `Restart-Computer` genererar ett icke-avslutande fel som **väntar** på den lokala datorn, men väntar på att fjärrdatorerna ska starta om.</span><span class="sxs-lookup"><span data-stu-id="c4635-248">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="c4635-249">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4635-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-250">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="c4635-250">-WsmanAuthentication</span></span>

<span data-ttu-id="c4635-251">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="c4635-251">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="c4635-252">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4635-252">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="c4635-253">De acceptabla värdena för den här parametern är: **Basic** , **CredSSP** , **default** , **Digest** , **Kerberos** och **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="c4635-253">The acceptable values for this parameter are: **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** , and **Negotiate**.</span></span>

<span data-ttu-id="c4635-254">Mer information finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="c4635-254">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="c4635-255">Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="c4635-255">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="c4635-256">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="c4635-256">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="c4635-257">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="c4635-257">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4635-258">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c4635-258">-Confirm</span></span>

<span data-ttu-id="c4635-259">Du uppmanas att bekräfta innan du kör `Restart-Computer` .</span><span class="sxs-lookup"><span data-stu-id="c4635-259">Prompts you for confirmation before running `Restart-Computer`.</span></span>

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

### <span data-ttu-id="c4635-260">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c4635-260">-WhatIf</span></span>

<span data-ttu-id="c4635-261">Visar vad som händer om `Restart-Computer` körningarna körs.</span><span class="sxs-lookup"><span data-stu-id="c4635-261">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="c4635-262">`Restart-Computer`Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="c4635-262">The `Restart-Computer` cmdlet isn't run.</span></span>

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

### <span data-ttu-id="c4635-263">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4635-263">CommonParameters</span></span>

<span data-ttu-id="c4635-264">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c4635-264">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4635-265">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c4635-265">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4635-266">INDATA</span><span class="sxs-lookup"><span data-stu-id="c4635-266">INPUTS</span></span>

### <span data-ttu-id="c4635-267">System. String</span><span class="sxs-lookup"><span data-stu-id="c4635-267">System.String</span></span>

<span data-ttu-id="c4635-268">`Restart-Computer` accepterar dator namn från pipelinen eller variablerna.</span><span class="sxs-lookup"><span data-stu-id="c4635-268">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

<span data-ttu-id="c4635-269">I Windows PowerShell 2,0 tar parametern **computername** in från pipelinen endast efter egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="c4635-269">In Windows PowerShell 2.0, the **ComputerName** parameter takes input from the pipeline only by property name.</span></span> <span data-ttu-id="c4635-270">I Windows PowerShell 3,0 och senare tas parametern **computername** in från pipelinen efter värde.</span><span class="sxs-lookup"><span data-stu-id="c4635-270">In Windows PowerShell 3.0, and later, the **ComputerName** parameter takes input from the pipeline by value.</span></span>

## <span data-ttu-id="c4635-271">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c4635-271">OUTPUTS</span></span>

### <span data-ttu-id="c4635-272">Ingen, system. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="c4635-272">None, System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="c4635-273">Om du anger parametern **AsJob** `Restart-Computer` returneras ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="c4635-273">If you specify the **AsJob** parameter, `Restart-Computer` returns a job object.</span></span> <span data-ttu-id="c4635-274">Annars genereras inga utdata.</span><span class="sxs-lookup"><span data-stu-id="c4635-274">Otherwise, no output is generated.</span></span>

## <span data-ttu-id="c4635-275">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c4635-275">NOTES</span></span>

- <span data-ttu-id="c4635-276">`Restart-Computer` fungerar endast på datorer som kör Windows och kräver att WinRM och WMI stänger av ett system, inklusive det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="c4635-276">`Restart-Computer` only work on computers running Windows and requires WinRM and WMI to shutdown a system, including the local system.</span></span>
- <span data-ttu-id="c4635-277">`Restart-Computer` använder [Win32Shutdown-metoden](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) för [Win32_OperatingSystems](/windows/desktop/CIMWin32Prov/win32-operatingsystem) klassen Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="c4635-277">`Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span>  <span data-ttu-id="c4635-278">Den här metoden kräver att **SeShutdownPrivilege** -behörighet aktive ras för det användar konto som används för att starta om datorn.</span><span class="sxs-lookup"><span data-stu-id="c4635-278">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="c4635-279">I Windows PowerShell 2,0 fungerar inte **AsJob** -parametern som tillförlitlig när du startar om eller stoppar fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="c4635-279">In Windows PowerShell 2.0, the **AsJob** parameter doesn't work reliably when you are restarting or stopping remote computers.</span></span> <span data-ttu-id="c4635-280">I Windows PowerShell 3,0 ändras implementeringen för att lösa problemet.</span><span class="sxs-lookup"><span data-stu-id="c4635-280">In Windows PowerShell 3.0, the implementation is changed to resolve this problem.</span></span>

## <span data-ttu-id="c4635-281">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c4635-281">RELATED LINKS</span></span>

[<span data-ttu-id="c4635-282">Om Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="c4635-282">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="c4635-283">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="c4635-283">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="c4635-284">WS-Managementprotokollet</span><span class="sxs-lookup"><span data-stu-id="c4635-284">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
