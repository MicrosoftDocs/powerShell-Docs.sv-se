---
description: Beskriver hur du felsöker fjärråtgärder i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: b78f3004e316b6d4de1082b914970d3c8b56f955
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/29/2020
ms.locfileid: "93273500"
---
# <a name="about-remote-troubleshooting"></a><span data-ttu-id="09763-104">Om fjärrfelsökning</span><span class="sxs-lookup"><span data-stu-id="09763-104">About Remote Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="09763-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="09763-105">Short description</span></span>
<span data-ttu-id="09763-106">Beskriver hur du felsöker fjärråtgärder i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09763-106">Describes how to troubleshoot remote operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="09763-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="09763-107">Long description</span></span>

<span data-ttu-id="09763-108">I det här avsnittet beskrivs några av de problem som du kan stöta på när du använder funktionerna för fjärr kommunikation i PowerShell som baseras på WS-Management teknik och det föreslår lösningar för dessa problem.</span><span class="sxs-lookup"><span data-stu-id="09763-108">This section describes some of the problems that you might encounter when using the remoting features of PowerShell that are based on WS-Management technology and it suggests solutions to these problems.</span></span>

<span data-ttu-id="09763-109">Innan du använder PowerShell-fjärrkommunikation, se [about_Remote](about_remote.md) och [about_Remote_Requirements](about_Remote_Requirements.md) för vägledning om konfiguration och grundläggande användning.</span><span class="sxs-lookup"><span data-stu-id="09763-109">Before using PowerShell remoting, see [about_Remote](about_remote.md) and [about_Remote_Requirements](about_Remote_Requirements.md) for guidance on configuration and basic use.</span></span> <span data-ttu-id="09763-110">Hjälp avsnitten för var och en av de olika cmdletarna för fjärr kommunikation, särskilt parameter beskrivningar, har också användbar information som är utformad för att hjälpa dig att undvika problem.</span><span class="sxs-lookup"><span data-stu-id="09763-110">Also, the Help topics for each of the remoting cmdlets, particularly the parameter descriptions, have useful information that is designed to help you avoid problems.</span></span>

> [!NOTE]
> <span data-ttu-id="09763-111">Om du vill visa eller ändra inställningarna för den lokala datorn i WSMan:-enheten, inklusive ändringar i sessionens konfigurationer, betrodda värdar, portar eller lyssnare, startar du PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="09763-111">To view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="troubleshooting-permission-and-authentication-issues"></a><span data-ttu-id="09763-112">Fel sökning av problem med behörighet och autentisering</span><span class="sxs-lookup"><span data-stu-id="09763-112">Troubleshooting permission and authentication issues</span></span>

<span data-ttu-id="09763-113">I det här avsnittet beskrivs fjärrstyrda problem som är relaterade till användar-och dator behörigheter och krav för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="09763-113">This section discusses remoting problems that are related to user and computer permissions and remoting requirements.</span></span>

### <a name="how-to-run-as-administrator"></a><span data-ttu-id="09763-114">Så här kör du som administratör</span><span class="sxs-lookup"><span data-stu-id="09763-114">How to run as administrator</span></span>

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

<span data-ttu-id="09763-115">Om du vill starta en fjärrsession på den lokala datorn eller Visa eller ändra inställningarna för den lokala datorn i WSMan: Drive, inklusive ändringar i sessionsinställningar, betrodda värdar, portar eller lyssnare, startar du Windows PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="09763-115">To start a remote session on the local computer, or to view or change settings for the local computer in the WSMan: drive, including changes to the session configurations, trusted hosts, ports, or listeners, start Windows PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="09763-116">Starta Windows PowerShell med alternativet **Kör som administratör** :</span><span class="sxs-lookup"><span data-stu-id="09763-116">To start Windows PowerShell with the **Run as administrator** option:</span></span>

- <span data-ttu-id="09763-117">Högerklicka på en Windows PowerShell-ikon (eller Windows PowerShell ISE) och klicka sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="09763-117">Right-click a Windows PowerShell (or Windows PowerShell ISE) icon and then click **Run as administrator**.</span></span>

  <span data-ttu-id="09763-118">Starta Windows PowerShell med alternativet **Kör som administratör** i Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="09763-118">To start Windows PowerShell with the **Run as administrator** option in Windows 7 and Windows Server 2008 R2.</span></span>

- <span data-ttu-id="09763-119">Högerklicka på Windows PowerShell-ikonen i aktivitets fältet i Windows och klicka sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="09763-119">In the Windows taskbar, right-click the Windows PowerShell icon, and then click **Run as administrator**.</span></span>

  <span data-ttu-id="09763-120">I Windows Server 2008 R2 fästs Windows PowerShell-ikonen i aktivitets fältet som standard.</span><span class="sxs-lookup"><span data-stu-id="09763-120">In Windows Server 2008 R2, the Windows PowerShell icon is pinned to the taskbar by default.</span></span>

### <a name="how-to-enable-remoting"></a><span data-ttu-id="09763-121">Så här aktiverar du fjärr kommunikation</span><span class="sxs-lookup"><span data-stu-id="09763-121">How to enable remoting</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

<span data-ttu-id="09763-122">Ingen konfiguration krävs för att en dator ska kunna skicka fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="09763-122">No configuration is required to enable a computer to send remote commands.</span></span>
<span data-ttu-id="09763-123">Men för att ta emot fjärrkommandon måste PowerShell-fjärrkommunikation vara aktiverat på datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-123">However, to receive remote commands, PowerShell remoting must be enabled on the computer.</span></span> <span data-ttu-id="09763-124">Genom att aktivera kan du starta WinRM-tjänsten, ange start typen för WinRM-tjänsten till automatisk, skapa lyssnare för HTTP-och HTTPS-anslutningar och skapa standardkonfigurationer för sessioner.</span><span class="sxs-lookup"><span data-stu-id="09763-124">Enabling includes starting the WinRM service, setting the startup type for the WinRM service to Automatic, creating listeners for HTTP and HTTPS connections, and creating default session configurations.</span></span>

<span data-ttu-id="09763-125">Windows PowerShell-fjärrkommunikation är aktiverat på Windows Server 2012 och senare versioner av Windows Server som standard.</span><span class="sxs-lookup"><span data-stu-id="09763-125">Windows PowerShell remoting is enabled on Windows Server 2012 and newer releases of Windows Server by default.</span></span> <span data-ttu-id="09763-126">Kör cmdleten på alla andra system `Enable-PSRemoting` för att aktivera fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="09763-126">On all other systems, run the `Enable-PSRemoting` cmdlet to enable remoting.</span></span> <span data-ttu-id="09763-127">Du kan också köra `Enable-PSRemoting` cmdleten för att återaktivera fjärr kommunikation på Windows server 2012 och nyare versioner av Windows Server om fjärr kommunikation är inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="09763-127">You can also run the `Enable-PSRemoting` cmdlet to re-enable remoting on Windows Server 2012 and newer releases of Windows Server if remoting is disabled.</span></span>

<span data-ttu-id="09763-128">Använd cmdleten om du vill konfigurera en dator för att ta emot fjärrkommandon `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="09763-128">To configure a computer to receive remote commands, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="09763-129">Följande kommando aktiverar alla nödvändiga Fjärrinställningar, aktiverar sessionsinställningar och startar om WinRM-tjänsten för att ändringarna ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="09763-129">The following command enables all required remote settings, enables the session configurations, and restarts the WinRM service to make the changes effective.</span></span>

`Enable-PSRemoting`

<span data-ttu-id="09763-130">Om du vill utelämna alla användar meddelanden skriver du:</span><span class="sxs-lookup"><span data-stu-id="09763-130">To suppress all user prompts, type:</span></span>

`Enable-PSRemoting -Force`

<span data-ttu-id="09763-131">Mer information finns i [enable-psremoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting).</span><span class="sxs-lookup"><span data-stu-id="09763-131">For more information, see [Enable-PSRemoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting).</span></span>

### <a name="how-to-enable-remoting-in-an-enterprise"></a><span data-ttu-id="09763-132">Så här aktiverar du fjärr kommunikation i ett företag</span><span class="sxs-lookup"><span data-stu-id="09763-132">How to enable remoting in an enterprise</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="09763-133">Använd cmdleten om du vill göra det möjligt för en enstaka dator att ta emot PowerShell-kommandon för fjärrkörning och acceptera anslutningar `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="09763-133">To enable a single computer to receive remote PowerShell commands and accept connections, use the `Enable-PSRemoting` cmdlet.</span></span>

<span data-ttu-id="09763-134">Om du vill aktivera fjärr kommunikation för flera datorer i ett företag kan du använda följande skalade alternativ.</span><span class="sxs-lookup"><span data-stu-id="09763-134">To enable remoting for multiple computers in an enterprise, you can use the following scaled options.</span></span>

- <span data-ttu-id="09763-135">Om du vill konfigurera lyssnare för fjärr kommunikation aktiverar du grup principen **Tillåt automatisk konfiguration av lyssnare** .</span><span class="sxs-lookup"><span data-stu-id="09763-135">To configure listeners for remoting, enable the **Allow automatic configuration of listeners** group policy.</span></span>

- <span data-ttu-id="09763-136">Använd cmdleten för att ange starttyp för Windows Remote Management (WinRM) till automatiskt på flera datorer `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="09763-136">To set the startup type of the Windows Remote Management (WinRM) to Automatic on multiple computers, use the `Set-Service` cmdlet.</span></span>

- <span data-ttu-id="09763-137">Om du vill aktivera ett brand Väggs undantag använder du **Windows-brand väggen: Tillåt lokala port undantag** grup principer.</span><span class="sxs-lookup"><span data-stu-id="09763-137">To enable a firewall exception, use the **Windows Firewall: Allow Local Port Exceptions** group policy.</span></span>

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a><span data-ttu-id="09763-138">Så här aktiverar du lyssnare med hjälp av en grup princip</span><span class="sxs-lookup"><span data-stu-id="09763-138">How to enable listeners by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="09763-139">Om du vill konfigurera lyssnarna för alla datorer i en domän aktiverar du inställningen **Tillåt automatisk konfiguration av Listener** i följande grupprincip sökväg:</span><span class="sxs-lookup"><span data-stu-id="09763-139">To configure the listeners for all computers in a domain, enable the **Allow automatic configuration of listeners** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

<span data-ttu-id="09763-140">Aktivera principen och ange IPv4-och IPv6-filter.</span><span class="sxs-lookup"><span data-stu-id="09763-140">Enable the policy and specify the IPv4 and IPv6 filters.</span></span> <span data-ttu-id="09763-141">Jokertecken ( `*` ) är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="09763-141">Wildcards (`*`) are permitted.</span></span>

### <a name="how-to-enable-remoting-on-public-networks"></a><span data-ttu-id="09763-142">Så här aktiverar du fjärr kommunikation i offentliga nätverk</span><span class="sxs-lookup"><span data-stu-id="09763-142">How to enable remoting on public networks</span></span>

```
ERROR:  Unable to check the status of the firewall
```

<span data-ttu-id="09763-143">`Enable-PSRemoting`Cmdleten returnerar det här felet när det lokala nätverket är offentligt och **SkipNetworkProfileCheck** -parametern inte används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="09763-143">The `Enable-PSRemoting` cmdlet returns this error when the local network is public and the **SkipNetworkProfileCheck** parameter is not used in the command.</span></span>

<span data-ttu-id="09763-144">På Server versioner av Windows `Enable-PSRemoting` lyckas alla typer av nätverks platser.</span><span class="sxs-lookup"><span data-stu-id="09763-144">On server versions of Windows, `Enable-PSRemoting` succeeds on all network location types.</span></span> <span data-ttu-id="09763-145">Den skapar brand Väggs regler som tillåter fjärråtkomst till privata nätverk och domän nätverk ("hem" och "arbets").</span><span class="sxs-lookup"><span data-stu-id="09763-145">It creates firewall rules that allow remote access to private and domain ("Home" and "Work") networks.</span></span> <span data-ttu-id="09763-146">För offentliga nätverk skapas brand Väggs regler som tillåter fjärråtkomst från samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="09763-146">For public networks, it creates firewall rules that allows remote access from the same local subnet.</span></span>

<span data-ttu-id="09763-147">På klient versioner av Windows fungerar `Enable-PSRemoting` i privata nätverk och domän nätverk.</span><span class="sxs-lookup"><span data-stu-id="09763-147">On client versions of Windows, `Enable-PSRemoting` succeeds on private and domain networks.</span></span> <span data-ttu-id="09763-148">Som standard Miss lyckas det på offentliga nätverk, men om du använder parametern **SkipNetworkProfileCheck** `Enable-PSRemoting` slutförs och skapas en brand Väggs regel som tillåter trafik från samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="09763-148">By default, it fails on public networks, but if you use the **SkipNetworkProfileCheck** parameter, `Enable-PSRemoting` succeeds and creates a firewall rule that allows traffic from the same local subnet.</span></span>

<span data-ttu-id="09763-149">Om du vill ta bort begränsningen för lokal undernät i offentliga nätverk och tillåta fjärråtkomst från vilken plats som helst, kör du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="09763-149">To remove the local subnet restriction on public networks and allow remote access from any location, run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="09763-150">`Set-NetFirewallRule`Cmdleten exporteras av Netsecurity-modulen.</span><span class="sxs-lookup"><span data-stu-id="09763-150">The `Set-NetFirewallRule` cmdlet is exported by the NetSecurity module.</span></span>

> [!NOTE]
> <span data-ttu-id="09763-151">På datorer som kör Server versioner av Windows i Windows PowerShell 2,0 `Enable-PSRemoting` skapar brand Väggs regler som tillåter fjärråtkomst i privata, domän-och offentliga nätverk.</span><span class="sxs-lookup"><span data-stu-id="09763-151">In Windows PowerShell 2.0, on computers running server versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access on private, domain and public networks.</span></span> <span data-ttu-id="09763-152">På datorer som kör klient versioner av Windows `Enable-PSRemoting` skapar brand Väggs regler som endast tillåter fjärråtkomst i privata nätverk och domän nätverk.</span><span class="sxs-lookup"><span data-stu-id="09763-152">On computers running client versions of Windows, `Enable-PSRemoting` creates firewall rules that allow remote access only on private and domain networks.</span></span>

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a><span data-ttu-id="09763-153">Så här aktiverar du ett brand Väggs undantag med en grup princip</span><span class="sxs-lookup"><span data-stu-id="09763-153">How to enable a firewall exception by using a group policy</span></span>

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="09763-154">Aktivera ett brand Väggs undantag för på alla datorer i en domän genom att aktivera **Windows-brand väggen: Tillåt lokal port undantags** princip i följande grupprincip sökväg:</span><span class="sxs-lookup"><span data-stu-id="09763-154">To enable a firewall exception for in all computers in a domain, enable the **Windows Firewall: Allow local port exceptions** policy in the following Group Policy path:</span></span>

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

<span data-ttu-id="09763-155">Med den här principen kan medlemmar i gruppen Administratörer på datorn använda **Windows-brandväggen** i **kontroll panelen** för att skapa ett brand Väggs undantag för tjänsten Windows Remote Management.</span><span class="sxs-lookup"><span data-stu-id="09763-155">This policy allows members of the Administrators group on the computer to use **Windows Firewall** in **Control Panel** to create a firewall exception for the Windows Remote Management service.</span></span>

<span data-ttu-id="09763-156">Om princip konfigurationen är felaktig kan följande fel meddelande visas:</span><span class="sxs-lookup"><span data-stu-id="09763-156">If the policy configuration is incorrect you may receive the following error:</span></span>

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

<span data-ttu-id="09763-157">Ett konfigurations fel i principen resulterar i ett tomt värde för egenskapen **ListeningOn** .</span><span class="sxs-lookup"><span data-stu-id="09763-157">A configuration error in the policy results in an empty value for the **ListeningOn** property.</span></span> <span data-ttu-id="09763-158">Använd följande kommando för att kontrol lera värdet.</span><span class="sxs-lookup"><span data-stu-id="09763-158">Use the following command to check the value.</span></span>

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a><span data-ttu-id="09763-159">Ange starttyp för WinRM-tjänsten</span><span class="sxs-lookup"><span data-stu-id="09763-159">How to set the startup type of the WinRM service</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="09763-160">PowerShell-fjärrkommunikation beror på WinRM-tjänsten (Windows Remote Management).</span><span class="sxs-lookup"><span data-stu-id="09763-160">PowerShell remoting depends upon the Windows Remote Management (WinRM) service.</span></span>
<span data-ttu-id="09763-161">Tjänsten måste köras för att stödja fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="09763-161">The service must be running to support remote commands.</span></span>

<span data-ttu-id="09763-162">I Server versioner av Windows är start typen för WinRM-tjänsten (Windows Remote Management) automatisk.</span><span class="sxs-lookup"><span data-stu-id="09763-162">On server versions of Windows, the startup type of the Windows Remote Management (WinRM) service is Automatic.</span></span>

<span data-ttu-id="09763-163">I klient versioner av Windows är WinRM-tjänsten dock inaktive rad som standard.</span><span class="sxs-lookup"><span data-stu-id="09763-163">However, on client versions of Windows, the WinRM service is disabled by default.</span></span>

<span data-ttu-id="09763-164">Använd cmdleten om du vill ange starttyp för en tjänst på en fjärrdator `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="09763-164">To set the startup type of a service on a remote computer, use the `Set-Service` cmdlet.</span></span>

<span data-ttu-id="09763-165">Om du vill köra kommandot på flera datorer kan du skapa en textfil eller en CSV-fil med dator namnen.</span><span class="sxs-lookup"><span data-stu-id="09763-165">To run the command on multiple computers, you can create a text file or CSV file of the computer names.</span></span>

<span data-ttu-id="09763-166">Följande kommandon får till exempel en lista över dator namn från `Servers.txt` filen och anger sedan start typen för WinRM-tjänsten på alla datorer till **Automatisk**.</span><span class="sxs-lookup"><span data-stu-id="09763-166">For example, the following commands get a list of computer names from the `Servers.txt` file and then sets the startup type of the WinRM service on all of the computers to **Automatic**.</span></span>

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

<span data-ttu-id="09763-167">Om du vill se resultatet använder du- `Get-WMIObject` cmdleten med **Win32_Service** -objektet.</span><span class="sxs-lookup"><span data-stu-id="09763-167">To see the results use the `Get-WMIObject` cmdlet with the **Win32_Service** object.</span></span> <span data-ttu-id="09763-168">Mer information finns i [set-service](xref:Microsoft.PowerShell.Management.Set-Service).</span><span class="sxs-lookup"><span data-stu-id="09763-168">For more information, see [Set-Service](xref:Microsoft.PowerShell.Management.Set-Service).</span></span>

### <a name="how-to-recreate-the-default-session-configurations"></a><span data-ttu-id="09763-169">Återskapa standardkonfigurationerna för sessioner</span><span class="sxs-lookup"><span data-stu-id="09763-169">How to recreate the default session configurations</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="09763-170">För att ansluta till den lokala datorn och köra kommandon via fjärr anslutning måste den lokala datorn innehålla konfigurationer för fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="09763-170">To connect to the local computer and run commands remotely, the local computer must include session configurations for remote commands.</span></span>

<span data-ttu-id="09763-171">När du använder `Enable-PSRemoting` skapas standardkonfigurationer för sessioner på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-171">When you use `Enable-PSRemoting`, it creates default session configurations on the local computer.</span></span> <span data-ttu-id="09763-172">Fjärranslutna användare använder dessa sessionsinställningar när ett fjärrkommando inte innehåller parametern **ConfigurationName** .</span><span class="sxs-lookup"><span data-stu-id="09763-172">Remote users use these session configurations whenever a remote command does not include the **ConfigurationName** parameter.</span></span>

<span data-ttu-id="09763-173">Om standard konfigurationerna på en dator är oregistrerade eller borttagna använder du `Enable-PSRemoting` cmdleten för att återskapa dem.</span><span class="sxs-lookup"><span data-stu-id="09763-173">If the default configurations on a computer are unregistered or deleted, use the `Enable-PSRemoting` cmdlet to recreate them.</span></span> <span data-ttu-id="09763-174">Du kan använda den här cmdleten upprepade gånger.</span><span class="sxs-lookup"><span data-stu-id="09763-174">You can use this cmdlet repeatedly.</span></span> <span data-ttu-id="09763-175">Det genererar inga fel om en funktion redan har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="09763-175">It does not generate errors if a feature is already configured.</span></span>

<span data-ttu-id="09763-176">Om du ändrar standardkonfigurationerna för sessioner och vill återställa de ursprungliga standardsessionerna, använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort de ändrade sessionerna och använder sedan `Enable-PSRemoting` cmdlet: en för att återställa dem.</span><span class="sxs-lookup"><span data-stu-id="09763-176">If you change the default session configurations and want to restore the original default session configurations, use the `Unregister-PSSessionConfiguration` cmdlet to delete the changed session configurations and then use the `Enable-PSRemoting` cmdlet to restore them.</span></span>
<span data-ttu-id="09763-177">`Enable-PSRemoting` ändrar inte befintliga konfigurationer för sessioner.</span><span class="sxs-lookup"><span data-stu-id="09763-177">`Enable-PSRemoting` does not change existing session configurations.</span></span>

> [!NOTE]
> <span data-ttu-id="09763-178">När `Enable-PSRemoting` återställer standardsessionens konfiguration, skapar den inte uttryckliga säkerhets beskrivningar för konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="09763-178">When `Enable-PSRemoting` restores the default session configuration, it does not create explicit security descriptors for the configurations.</span></span> <span data-ttu-id="09763-179">I stället ärver konfigurationerna säkerhets beskrivningen för RootSDDL, som är säker som standard.</span><span class="sxs-lookup"><span data-stu-id="09763-179">Instead, the configurations inherit the security descriptor of the RootSDDL, which is secure by default.</span></span>

<span data-ttu-id="09763-180">Om du vill se säkerhets beskrivningen RootSDDL skriver du:</span><span class="sxs-lookup"><span data-stu-id="09763-180">To see the RootSDDL security descriptor, type:</span></span>

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

<span data-ttu-id="09763-181">Om du vill ändra RootSDDL använder du `Set-Item` cmdleten i kommandot WSMan: Drive.</span><span class="sxs-lookup"><span data-stu-id="09763-181">To change the RootSDDL, use the `Set-Item` cmdlet in the WSMan: drive.</span></span> <span data-ttu-id="09763-182">Om du vill ändra säkerhets beskrivningen för en sessions konfiguration använder du `Set-PSSessionConfiguration` cmdleten med parametrarna **SecurityDescriptorSDDL** eller **ShowSecurityDescriptorUI** .</span><span class="sxs-lookup"><span data-stu-id="09763-182">To change the security descriptor of a session configuration, use the `Set-PSSessionConfiguration` cmdlet with the **SecurityDescriptorSDDL** or **ShowSecurityDescriptorUI** parameters.</span></span>

<span data-ttu-id="09763-183">Mer information om WSMan:-enheten finns i hjälp avsnittet för WSMan-providern ("Get-Help WSMan").</span><span class="sxs-lookup"><span data-stu-id="09763-183">For more information about the WSMan: drive, see the Help topic for the WSMan provider ("Get-Help wsman").</span></span>

### <a name="how-to-provide-administrator-credentials"></a><span data-ttu-id="09763-184">Ange administratörsautentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="09763-184">How to provide administrator credentials</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="09763-185">Om du vill skapa en PSSession eller köra kommandon på en fjärrdator, som standard, måste den aktuella användaren vara medlem i gruppen Administratörer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="09763-185">To create a PSSession or run commands on a remote computer, by default, the current user must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="09763-186">Autentiseringsuppgifter krävs ibland även när den aktuella användaren är inloggad på ett konto som är medlem i gruppen Administratörer.</span><span class="sxs-lookup"><span data-stu-id="09763-186">Credentials are sometimes required even when the current user is logged on to an account that is a member of the Administrators group.</span></span>

<span data-ttu-id="09763-187">Om den aktuella användaren är medlem i gruppen Administratörer på fjärrdatorn, eller om du kan ange autentiseringsuppgifter för en medlem i gruppen Administratörer, använder du parametern **Credential** för `New-PSSession` - `Enter-PSSession` eller-cmdlet: `Invoke-Command` ar för att fjärrans luta.</span><span class="sxs-lookup"><span data-stu-id="09763-187">If the current user is a member of the Administrators group on the remote computer, or can provide the credentials of a member of the Administrators group, use the **Credential** parameter of the `New-PSSession`, `Enter-PSSession` or `Invoke-Command` cmdlets to connect remotely.</span></span>

<span data-ttu-id="09763-188">Följande kommando innehåller till exempel autentiseringsuppgifterna för en administratör.</span><span class="sxs-lookup"><span data-stu-id="09763-188">For example, the following command provides the credentials of an Administrator.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="09763-189">Mer information om parametern för **autentiseringsuppgifter** finns i [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [RETUR-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) eller [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command).</span><span class="sxs-lookup"><span data-stu-id="09763-189">For more information about the **Credential** parameter, see [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command).</span></span>

### <a name="how-to-enable-remoting-for-non-administrative-users"></a><span data-ttu-id="09763-190">Så här aktiverar du fjärr kommunikation för icke-administrativa användare</span><span class="sxs-lookup"><span data-stu-id="09763-190">How to enable remoting for non-administrative users</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="09763-191">Om du vill upprätta en PSSession eller köra ett kommando på en fjärrdator måste användaren ha behörighet att använda sessionens konfigurationer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="09763-191">To establish a PSSession or run a command on a remote computer, the user must have permission to use the session configurations on the remote computer.</span></span>

<span data-ttu-id="09763-192">Som standard har bara medlemmar i gruppen Administratörer på en dator behörighet att använda standardkonfigurationerna för sessioner.</span><span class="sxs-lookup"><span data-stu-id="09763-192">By default, only members of the Administrators group on a computer have permission to use the default session configurations.</span></span> <span data-ttu-id="09763-193">Därför kan endast medlemmar i gruppen Administratörer fjärrans luta till datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-193">Therefore, only members of the Administrators group can connect to the computer remotely.</span></span>

<span data-ttu-id="09763-194">Om du vill att andra användare ska kunna ansluta till den lokala datorn ger du användaren körnings behörighet till standardkonfigurationerna för sessioner på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-194">To allow other users to connect to the local computer, give the user Execute permissions to the default session configurations on the local computer.</span></span>

<span data-ttu-id="09763-195">Följande kommando öppnar en egenskaps sida där du kan ändra säkerhets beskrivningen för standard konfigurationen av Microsoft. PowerShell-sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-195">The following command opens a property sheet that lets you change the security descriptor of the default Microsoft.PowerShell session configuration on the local computer.</span></span>

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

<span data-ttu-id="09763-196">Mer information finns i [about_Session_Configurations](about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="09763-196">For more information, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a><span data-ttu-id="09763-197">Så här aktiverar du fjärr kommunikation för administratörer i andra domäner</span><span class="sxs-lookup"><span data-stu-id="09763-197">How to enable remoting for administrators in other domains</span></span>

```
ERROR:  ACCESS IS DENIED
```

<span data-ttu-id="09763-198">När en användare i en annan domän är medlem i gruppen Administratörer på den lokala datorn kan användaren inte fjärrans luta till den lokala datorn med administratörs behörighet.</span><span class="sxs-lookup"><span data-stu-id="09763-198">When a user in another domain is a member of the Administrators group on the local computer, the user cannot connect to the local computer remotely with Administrator privileges.</span></span> <span data-ttu-id="09763-199">Som standard körs fjärr anslutningar från andra domäner med bara standard-token för användar behörighet.</span><span class="sxs-lookup"><span data-stu-id="09763-199">By default, remote connections from other domains run with only standard user privilege tokens.</span></span>

<span data-ttu-id="09763-200">Du kan dock använda register posten **LocalAccountTokenFilterPolicy** för att ändra standard beteendet och tillåta att fjärran vändare som är medlemmar i gruppen Administratörer kan köra med administratörs behörighet.</span><span class="sxs-lookup"><span data-stu-id="09763-200">However, you can use the **LocalAccountTokenFilterPolicy** registry entry to change the default behavior and allow remote users who are members of the Administrators group to run with Administrator privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="09763-201">**LocalAccountTokenFilterPolicy** -posten inaktiverar fjärrbegränsningar för User Account Control (UAC) för alla användare av alla berörda datorer.</span><span class="sxs-lookup"><span data-stu-id="09763-201">The **LocalAccountTokenFilterPolicy** entry disables user account control (UAC) remote restrictions for all users of all affected computers.</span></span> <span data-ttu-id="09763-202">Ta hänsyn till konsekvenserna av den här inställningen noggrant innan du ändrar principen.</span><span class="sxs-lookup"><span data-stu-id="09763-202">Consider the implications of this setting carefully before changing the policy.</span></span>

<span data-ttu-id="09763-203">Om du vill ändra principen använder du följande kommando för att ange värdet för register posten **LocalAccountTokenFilterPolicy** till 1.</span><span class="sxs-lookup"><span data-stu-id="09763-203">To change the policy, use the following command to set the value of the **LocalAccountTokenFilterPolicy** registry entry to 1.</span></span>

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a><span data-ttu-id="09763-204">Använda en IP-adress i ett fjärran slutet kommando</span><span class="sxs-lookup"><span data-stu-id="09763-204">How to use an ip address in a remote command</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="09763-205">Parametern **computername** för `New-PSSession` `Enter-PSSession` `Invoke-Command` CMDLETarna och accepterar en IP-adress som ett giltigt värde.</span><span class="sxs-lookup"><span data-stu-id="09763-205">The **ComputerName** parameter of the `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets accepts an IP address as a valid value.</span></span> <span data-ttu-id="09763-206">Men eftersom Kerberos-autentisering inte stöder IP-adresser används NTLM-autentisering som standard när du anger en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="09763-206">However, because Kerberos authentication does not support IP addresses, NTLM authentication is used by default whenever you specify an IP address.</span></span>

<span data-ttu-id="09763-207">När du använder NTLM-autentisering krävs följande procedur för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="09763-207">When using NTLM authentication, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="09763-208">Konfigurera datorn för HTTPS-transport eller Lägg till IP-adresserna för fjärrdatorerna i listan TrustedHosts på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-208">Configure the computer for HTTPS transport or add the IP addresses of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="09763-209">Använd parametern **Credential** i alla fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="09763-209">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="09763-210">Detta krävs även när du skickar in autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="09763-210">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a><span data-ttu-id="09763-211">Fjärrans luta från en arbets grupps dator</span><span class="sxs-lookup"><span data-stu-id="09763-211">How to connect remotely from a workgroup-based computer</span></span>

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

<span data-ttu-id="09763-212">Om den lokala datorn inte finns i en domän krävs följande procedur för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="09763-212">When the local computer is not in a domain, the following procedure is required for remoting.</span></span>

1. <span data-ttu-id="09763-213">Konfigurera datorn för HTTPS-transport eller Lägg till namnen på fjärrdatorerna i listan TrustedHosts på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-213">Configure the computer for HTTPS transport or add the names of the remote computers to the TrustedHosts list on the local computer.</span></span>

1. <span data-ttu-id="09763-214">Kontrol lera att ett lösen ord har angetts på den arbets grupps dator.</span><span class="sxs-lookup"><span data-stu-id="09763-214">Verify that a password is set on the workgroup-based computer.</span></span> <span data-ttu-id="09763-215">Om inget lösen ord har angetts eller om lösen ordet är tomt kan du inte köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="09763-215">If a password is not set or the password value is empty, you cannot run remote commands.</span></span>

   <span data-ttu-id="09763-216">Ange lösen ordet för ditt användar konto med hjälp av användar konton på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="09763-216">To set password for your user account, use User Accounts in Control Panel.</span></span>

1. <span data-ttu-id="09763-217">Använd parametern **Credential** i alla fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="09763-217">Use the **Credential** parameter in all remote commands.</span></span>

   <span data-ttu-id="09763-218">Detta krävs även när du skickar in autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="09763-218">This is required even when you are submitting the credentials of the current user.</span></span>

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a><span data-ttu-id="09763-219">Så här lägger du till en dator i listan över betrodda värdar</span><span class="sxs-lookup"><span data-stu-id="09763-219">How to add a computer to the trusted hosts list</span></span>

<span data-ttu-id="09763-220">Objektet TrustedHosts kan innehålla en kommaavgränsad lista med dator namn, IP-adresser och fullständigt kvalificerade domän namn.</span><span class="sxs-lookup"><span data-stu-id="09763-220">The TrustedHosts item can contain a comma-separated list of computer names, IP addresses, and fully-qualified domain names.</span></span> <span data-ttu-id="09763-221">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="09763-221">Wildcards are permitted.</span></span>

<span data-ttu-id="09763-222">Om du vill visa eller ändra listan över betrodda värdar använder du kommandot WSMan: Drive.</span><span class="sxs-lookup"><span data-stu-id="09763-222">To view or change the trusted host list, use the WSMan: drive.</span></span> <span data-ttu-id="09763-223">TrustedHost-objektet finns i `WSMan:\localhost\Client` noden.</span><span class="sxs-lookup"><span data-stu-id="09763-223">The TrustedHost item is in the `WSMan:\localhost\Client` node.</span></span>

<span data-ttu-id="09763-224">Endast medlemmar i gruppen Administratörer på datorn har behörighet att ändra listan över betrodda värdar på datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-224">Only members of the Administrators group on the computer have permission to change the list of trusted hosts on the computer.</span></span>

<span data-ttu-id="09763-225">Varning! det värde som du anger för objektet TrustedHosts påverkar alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-225">Caution: The value that you set for the TrustedHosts item affects all users of the computer.</span></span>

<span data-ttu-id="09763-226">Använd följande kommando om du vill visa en lista över betrodda värdar:</span><span class="sxs-lookup"><span data-stu-id="09763-226">To view the list of trusted hosts, use the following command:</span></span>

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

<span data-ttu-id="09763-227">Du kan också använda `Set-Location` cmdleten (alias = CD) för att navigera om WSMan: enheten till platsen.</span><span class="sxs-lookup"><span data-stu-id="09763-227">You can also use the `Set-Location` cmdlet (alias = cd) to navigate though the WSMan: drive to the location.</span></span> <span data-ttu-id="09763-228">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="09763-228">For example:</span></span>

```powershell
cd WSMan:\localhost\Client; dir
```

<span data-ttu-id="09763-229">Om du vill lägga till alla datorer i listan över betrodda värdar använder du följande kommando, som placerar värdet \* (alla) i ComputerName</span><span class="sxs-lookup"><span data-stu-id="09763-229">To add all computers to the list of trusted hosts, use the following command, which places a value of \* (all) in the ComputerName</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

<span data-ttu-id="09763-230">Du kan också använda ett jokertecken ( `*` ) för att lägga till alla datorer i en viss domän i listan över betrodda värdar.</span><span class="sxs-lookup"><span data-stu-id="09763-230">You can also use a wildcard character (`*`) to add all computers in a particular domain to the list of trusted hosts.</span></span> <span data-ttu-id="09763-231">Följande kommando lägger till exempel till alla datorer i domänen fabrikam i listan över betrodda värdar.</span><span class="sxs-lookup"><span data-stu-id="09763-231">For example, the following command adds all of the computers in the Fabrikam domain to the list of trusted hosts.</span></span>

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

<span data-ttu-id="09763-232">Om du vill lägga till namnen på vissa datorer i listan över betrodda värdar, använder du följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="09763-232">To add the names of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

<span data-ttu-id="09763-233">där varje värde `<ComputerName>` måste ha följande format:</span><span class="sxs-lookup"><span data-stu-id="09763-233">where each value `<ComputerName>` must have the following format:</span></span>

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

<span data-ttu-id="09763-234">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="09763-234">For example:</span></span>

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

<span data-ttu-id="09763-235">Om du vill lägga till ett dator namn i en befintlig lista över betrodda värdar sparar du först det aktuella värdet i en variabel och anger sedan värdet till en kommaavgränsad lista som innehåller de aktuella och nya värdena.</span><span class="sxs-lookup"><span data-stu-id="09763-235">To add a computer name to an existing list of trusted hosts, first save the current value in a variable, and then set the value to a comma-separated list that includes the current and new values.</span></span>

<span data-ttu-id="09763-236">Om du till exempel vill lägga till Server01-datorn i en befintlig lista över betrodda värdar, använder du följande kommando</span><span class="sxs-lookup"><span data-stu-id="09763-236">For example, to add the Server01 computer to an existing list of trusted hosts, use the following command</span></span>

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

<span data-ttu-id="09763-237">Om du vill lägga till IP-adresserna för särskilda datorer i listan över betrodda värdar, använder du följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="09763-237">To add the IP addresses of particular computers to the list of trusted hosts, use the following command format:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

<span data-ttu-id="09763-238">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="09763-238">For example:</span></span>

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

<span data-ttu-id="09763-239">Om du vill lägga till en dator i listan TrustedHosts för en fjärrdator använder du `Connect-WSMan` cmdleten för att lägga till en nod för fjärrdatorn på enheten WSMan: på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-239">To add a computer to the TrustedHosts list of a remote computer, use the `Connect-WSMan` cmdlet to add a node for the remote computer to the WSMan: drive on the local computer.</span></span> <span data-ttu-id="09763-240">Använd sedan ett `Set-Item` kommando för att lägga till datorn.</span><span class="sxs-lookup"><span data-stu-id="09763-240">Then use a `Set-Item` command to add the computer.</span></span>

<span data-ttu-id="09763-241">Mer information om `Connect-WSMan` cmdleten finns i [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span><span class="sxs-lookup"><span data-stu-id="09763-241">For more information about the `Connect-WSMan` cmdlet, see [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span>

## <a name="troubleshooting-computer-configuration-issues"></a><span data-ttu-id="09763-242">Felsöka problem med dator konfiguration</span><span class="sxs-lookup"><span data-stu-id="09763-242">Troubleshooting computer configuration issues</span></span>

<span data-ttu-id="09763-243">I det här avsnittet beskrivs fjärrproblem som är relaterade till särskilda konfigurationer av en dator, domän eller företag.</span><span class="sxs-lookup"><span data-stu-id="09763-243">This section discusses remoting problems that are related to particular configurations of a computer, domain, or enterprise.</span></span>

### <a name="how-to-configure-remoting-on-alternate-ports"></a><span data-ttu-id="09763-244">Konfigurera fjärr kommunikation på alternativa portar</span><span class="sxs-lookup"><span data-stu-id="09763-244">How to configure remoting on alternate ports</span></span>

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

<span data-ttu-id="09763-245">PowerShell-fjärrkommunikation använder port 80 för HTTP-transport som standard.</span><span class="sxs-lookup"><span data-stu-id="09763-245">PowerShell remoting uses port 80 for HTTP transport by default.</span></span> <span data-ttu-id="09763-246">Standard porten används när användaren inte anger **ConnectionURI** eller **port** parametrar i ett fjärran slutet kommando.</span><span class="sxs-lookup"><span data-stu-id="09763-246">The default port is used whenever the user does not specify the **ConnectionURI** or **Port** parameters in a remote command.</span></span>

<span data-ttu-id="09763-247">Om du vill ändra standard porten som PowerShell använder använder `Set-Item` du cmdleten i WSMan: Drive för att ändra Portvärdet i noden lyssnare.</span><span class="sxs-lookup"><span data-stu-id="09763-247">To change the default port that PowerShell uses, use `Set-Item` cmdlet in the WSMan: drive to change the Port value in the listener leaf node.</span></span>

<span data-ttu-id="09763-248">Följande kommando ändrar till exempel standard porten till 8080.</span><span class="sxs-lookup"><span data-stu-id="09763-248">For example, the following command changes the default port to 8080.</span></span>

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a><span data-ttu-id="09763-249">Konfigurera fjärr kommunikation med en proxyserver</span><span class="sxs-lookup"><span data-stu-id="09763-249">How to configure remoting with a proxy server</span></span>

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

<span data-ttu-id="09763-250">Eftersom PowerShell-fjärrkommunikation använder HTTP-protokollet, påverkas det av HTTP-proxyinställningarna.</span><span class="sxs-lookup"><span data-stu-id="09763-250">Because PowerShell remoting uses the HTTP protocol, it is affected by HTTP proxy settings.</span></span> <span data-ttu-id="09763-251">I företag som har proxyservrar kan användarna inte komma åt en PowerShell-fjärrdator direkt.</span><span class="sxs-lookup"><span data-stu-id="09763-251">In enterprises that have proxy servers, users cannot access a PowerShell remote computer directly.</span></span>

<span data-ttu-id="09763-252">Lös problemet genom att använda alternativen för proxyservern i fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="09763-252">To resolve this problem, use proxy setting options in your remote command.</span></span> <span data-ttu-id="09763-253">Följande inställningar är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="09763-253">The following settings are available:</span></span>

- <span data-ttu-id="09763-254">ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="09763-254">ProxyAccessType</span></span>
- <span data-ttu-id="09763-255">ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="09763-255">ProxyAuthentication</span></span>
- <span data-ttu-id="09763-256">ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="09763-256">ProxyCredential</span></span>

<span data-ttu-id="09763-257">Använd följande procedur för att ange de här alternativen för ett visst kommando:</span><span class="sxs-lookup"><span data-stu-id="09763-257">To set these options for a particular command, use the following procedure:</span></span>

1. <span data-ttu-id="09763-258">Använd **ProxyAccessType** -, **ProxyAuthentication** -och **ProxyCredential** -parametrarna för `New-PSSessionOption` cmdlet: en för att skapa ett session-objekt med proxyinställningarna för ditt företag.</span><span class="sxs-lookup"><span data-stu-id="09763-258">Use the **ProxyAccessType** , **ProxyAuthentication** , and **ProxyCredential** parameters of the `New-PSSessionOption` cmdlet to create a session option object with the proxy settings for your enterprise.</span></span> <span data-ttu-id="09763-259">Spara objektet alternativ är en variabel.</span><span class="sxs-lookup"><span data-stu-id="09763-259">Save the option object is a variable.</span></span>

1. <span data-ttu-id="09763-260">Använd variabeln som innehåller option-objektet som värdet för **SessionOption** -parametern för ett `New-PSSession` , `Enter-PSSession` -eller- `Invoke-Command` kommando.</span><span class="sxs-lookup"><span data-stu-id="09763-260">Use the variable that contains the option object as the value of the **SessionOption** parameter of a `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` command.</span></span>

<span data-ttu-id="09763-261">Följande kommando skapar till exempel objektet Session-alternativ med alternativ för proxyautentisering och använder sedan objektet för att skapa en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="09763-261">For example, the following command creates a session option object with proxy session options and then uses the object to create a remote session.</span></span>

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

<span data-ttu-id="09763-262">Mer information om `New-PSSessionOption` cmdleten finns i [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="09763-262">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="09763-263">Om du vill ange de här alternativen för alla fjärrkommandon i den aktuella sessionen använder du alternativet objekt som `New-PSSessionOption` skapar i värdet för `$PSSessionOption` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="09763-263">To set these options for all remote commands in the current session, use the option object that `New-PSSessionOption` creates in the value of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="09763-264">Mer information finns i [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="09763-264">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="09763-265">Om du vill ange de här alternativen för alla fjärrkommandon alla PowerShell-sessioner på den lokala datorn lägger du till `$PSSessionOption` preferens-variabeln i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="09763-265">To set these options for all remote commands all PowerShell sessions on the local computer, add the `$PSSessionOption` preference variable to your PowerShell profile.</span></span> <span data-ttu-id="09763-266">Mer information om PowerShell-profiler finns [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="09763-266">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a><span data-ttu-id="09763-267">Så här identifierar du en 32-bitars session på en 64-bitars dator</span><span class="sxs-lookup"><span data-stu-id="09763-267">How to detect a 32-bit session on a 64-bit computer</span></span>

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="09763-268">Om fjärrdatorn kör en 64-bitars version av Windows och fjärrkommandot använder en 32-bitars konfiguration av sessionen, till exempel Microsoft. PowerShell32, Windows Remote Management (WinRM) läser in en WOW64-process och Windows omdirigerar automatiskt alla referenser till katalogen `$env:Windir\System32` till `$env:Windir\SysWOW64` katalogen.</span><span class="sxs-lookup"><span data-stu-id="09763-268">If the remote computer is running a 64-bit version of Windows, and the remote command is using a 32-bit session configuration, such as Microsoft.PowerShell32, Windows Remote Management (WinRM) loads a WOW64 process and Windows automatically redirects all references to the `$env:Windir\System32` directory to the `$env:Windir\SysWOW64` directory.</span></span>

<span data-ttu-id="09763-269">Det innebär att om du försöker använda verktyg i katalogen System32 som inte har motsvarigheter i katalogen SysWow64, till exempel `Defrag.exe` , går det inte att hitta verktygen i katalogen.</span><span class="sxs-lookup"><span data-stu-id="09763-269">As a result, if you try to use tools in the System32 directory that do not have counterparts in the SysWow64 directory, such as `Defrag.exe`, the tools cannot be found in the directory.</span></span>

<span data-ttu-id="09763-270">Om du vill hitta den processor arkitektur som används i sessionen använder du värdet för variabeln **PROCESSOR_ARCHITECTURE** .</span><span class="sxs-lookup"><span data-stu-id="09763-270">To find the processor architecture that is being used in the session, use the value of the **PROCESSOR_ARCHITECTURE** environment variable.</span></span> <span data-ttu-id="09763-271">Följande kommando hittar processor arkitekturen för sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="09763-271">The following command finds the processor architecture of the session in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

<span data-ttu-id="09763-272">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="09763-272">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="troubleshooting-policy-and-preference-issues"></a><span data-ttu-id="09763-273">Fel sökning av princip-och inställnings problem</span><span class="sxs-lookup"><span data-stu-id="09763-273">Troubleshooting policy and preference issues</span></span>

<span data-ttu-id="09763-274">I det här avsnittet beskrivs fjärrstyrda problem som är relaterade till principer och inställningar som anges på lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="09763-274">This section discusses remoting problems that are related to policies and preferences set on the local and remote computers.</span></span>

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a><span data-ttu-id="09763-275">Ändra körnings principen för Import-PSSession och Import-Module</span><span class="sxs-lookup"><span data-stu-id="09763-275">How to change the execution policy for Import-PSSession and Import-Module</span></span>

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

<span data-ttu-id="09763-276">`Import-PSSession` `Export-PSSession` Cmdletarna och skapar moduler som innehåller osignerade skriptfiler och formaterar filer.</span><span class="sxs-lookup"><span data-stu-id="09763-276">The `Import-PSSession` and `Export-PSSession` cmdlets create modules that contains unsigned script files and formatting files.</span></span>

<span data-ttu-id="09763-277">Om du vill importera moduler som skapats av dessa cmdlets, antingen med hjälp av `Import-PSSession` eller `Import-Module` , kan inte körnings principen i den aktuella sessionen vara begränsad eller AllSigned.</span><span class="sxs-lookup"><span data-stu-id="09763-277">To import the modules that are created by these cmdlets, either by using `Import-PSSession` or `Import-Module`, the execution policy in the current session cannot be Restricted or AllSigned.</span></span> <span data-ttu-id="09763-278">Information om körnings principer för PowerShell finns i [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="09763-278">For information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="09763-279">Om du vill importera modulerna utan att ändra körnings principen för den lokala datorn som anges i registret, använder du **omfattnings** parametern för `Set-ExecutionPolicy` att ange en mindre begränsande körnings princip för en enda process.</span><span class="sxs-lookup"><span data-stu-id="09763-279">To import the modules without changing the execution policy for the local computer that is set in the registry, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>

<span data-ttu-id="09763-280">Följande kommando startar till exempel en process med `RemoteSigned` körnings principen.</span><span class="sxs-lookup"><span data-stu-id="09763-280">For example, the following command starts a process with the `RemoteSigned` execution policy.</span></span> <span data-ttu-id="09763-281">Ändringen av körnings principen påverkar endast den aktuella processen och ändrar inte register inställningen för PowerShell- **ExecutionPolicy** .</span><span class="sxs-lookup"><span data-stu-id="09763-281">The execution policy change affects only the current process and does not change the PowerShell **ExecutionPolicy** registry setting.</span></span>

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="09763-282">Du kan också använda **ExecutionPolicy** -parametern för `PowerShell.exe` för att starta en enskild session med en mindre begränsande körnings princip.</span><span class="sxs-lookup"><span data-stu-id="09763-282">You can also use the **ExecutionPolicy** parameter of `PowerShell.exe` to start a single session with a less restrictive execution policy.</span></span>

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="09763-283">Mer information om körnings principer finns [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="09763-283">For more information about execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span> <span data-ttu-id="09763-284">För mer information ange `PowerShell.exe -?`.</span><span class="sxs-lookup"><span data-stu-id="09763-284">For more information, type `PowerShell.exe -?`.</span></span>

### <a name="how-to-set-and-change-quotas"></a><span data-ttu-id="09763-285">Ange och ändra kvoter</span><span class="sxs-lookup"><span data-stu-id="09763-285">How to set and change quotas</span></span>

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

<span data-ttu-id="09763-286">Du kan använda kvoter för att skydda den lokala datorn och fjärrdatorn från överdriven resursanvändning, både av misstag och skadlig.</span><span class="sxs-lookup"><span data-stu-id="09763-286">You can use quotas to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span>

<span data-ttu-id="09763-287">Följande kvoter är tillgängliga i den grundläggande konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="09763-287">The following quotas are available in the basic configuration.</span></span>

- <span data-ttu-id="09763-288">WSMan-providern (WSMan:) innehåller flera kvot inställningar, till exempel inställningarna **MaxEnvelopeSizeKB** och **MaxProviderRequests** i `WSMan:<ComputerName>` noden och inställningarna **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** och **MaxConnections** i `WSMan:<ComputerName>\Service` noden.</span><span class="sxs-lookup"><span data-stu-id="09763-288">The WSMan provider (WSMan:) provides several quota settings, such as the **MaxEnvelopeSizeKB** and **MaxProviderRequests** settings in the `WSMan:<ComputerName>` node and the **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** , and **MaxConnections** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="09763-289">Du kan skydda den lokala datorn med hjälp av parametrarna **MaximumReceivedDataSizePerCommand** och **MaximumReceivedObjectSize** för `New-PSSessionOption` cmdleten och `$PSSessionOption` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="09763-289">You can protect the local computer by using the **MaximumReceivedDataSizePerCommand** and **MaximumReceivedObjectSize** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="09763-290">Du kan skydda fjärrdatorn genom att lägga till begränsningar i sessionens konfigurationer, till exempel genom att använda parametrarna **MaximumReceivedDataSizePerCommandMB** och **MaximumReceivedObjectSizeMB** för `Register-PSSessionConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="09763-290">You can protect the remote computer by adding restrictions to the session configurations, such as by using the **MaximumReceivedDataSizePerCommandMB** and **MaximumReceivedObjectSizeMB** parameters of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="09763-291">När kvoter står i konflikt med ett kommando genererar PowerShell ett fel.</span><span class="sxs-lookup"><span data-stu-id="09763-291">When quotas conflict with a command, PowerShell generates an error.</span></span>

<span data-ttu-id="09763-292">Lös felet genom att ändra fjärrkommandot så att det följer kvoten.</span><span class="sxs-lookup"><span data-stu-id="09763-292">To resolve the error, change the remote command to comply with the quota.</span></span> <span data-ttu-id="09763-293">Eller Bestäm kvotens källa och öka sedan kvoten för att tillåta att kommandot slutförs.</span><span class="sxs-lookup"><span data-stu-id="09763-293">Or, determine the source of the quota, and then increase the quota to allow the command to complete.</span></span>

<span data-ttu-id="09763-294">Följande kommando ökar till exempel kvoten för objekt storlek i konfigurationen av Microsoft. PowerShell-sessionen på fjärrdatorn från 10 MB (standardvärdet) till 11 MB.</span><span class="sxs-lookup"><span data-stu-id="09763-294">For example, the following command increases the object size quota in the Microsoft.PowerShell session configuration on the remote computer from 10 MB (the default value) to 11 MB.</span></span>

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

<span data-ttu-id="09763-295">Mer information om `New-PSSessionOption` cmdleten finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="09763-295">For more information about the `New-PSSessionOption` cmdlet, see `New-PSSessionOption`.</span></span>

<span data-ttu-id="09763-296">Mer information om WS-Management kvoter finns [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="09763-296">For more information about the WS-Management quotas, see [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md).</span></span>

### <a name="how-to-resolve-timeout-errors"></a><span data-ttu-id="09763-297">Så här löser du timeout-fel</span><span class="sxs-lookup"><span data-stu-id="09763-297">How to resolve timeout errors</span></span>

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

<span data-ttu-id="09763-298">Du kan använda tids gränser för att skydda den lokala datorn och fjärrdatorn från överdriven resursanvändning, både av misstag och skadlig.</span><span class="sxs-lookup"><span data-stu-id="09763-298">You can use timeouts to protect the local computer and the remote computer from excessive resource use, both accidental and malicious.</span></span> <span data-ttu-id="09763-299">När timeout anges på både den lokala datorn och fjärrdatorn använder PowerShell de kortaste timeout-inställningarna.</span><span class="sxs-lookup"><span data-stu-id="09763-299">When timeouts are set on both the local and remote computer, PowerShell uses the shortest timeout settings.</span></span>

<span data-ttu-id="09763-300">Följande tids gränser är tillgängliga i den grundläggande konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="09763-300">The following timeouts are available in the basic configuration.</span></span>

- <span data-ttu-id="09763-301">WSMan-providern (WSMan:) innehåller flera tids gräns inställningar på klient sidan och på tjänst sidan, till exempel **MaxTimeoutms** -inställningen i `WSMan:<ComputerName>` noden och inställningarna **EnumerationTimeoutms** och **MaxPacketRetrievalTimeSeconds** i `WSMan:<ComputerName>\Service` noden.</span><span class="sxs-lookup"><span data-stu-id="09763-301">The WSMan provider (WSMan:) provides several client-side and service-side timeout settings, such as the **MaxTimeoutms** setting in the `WSMan:<ComputerName>` node and the **EnumerationTimeoutms** and **MaxPacketRetrievalTimeSeconds** settings in the `WSMan:<ComputerName>\Service` node.</span></span>

- <span data-ttu-id="09763-302">Du kan skydda den lokala datorn med hjälp av parametrarna **CancelTimeout** , **idleTimeout** , **opentimey** och **OperationTimeout** för `New-PSSessionOption` cmdleten och `$PSSessionOption` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="09763-302">You can protect the local computer by using the **CancelTimeout** , **IdleTimeout** , **OpenTimeout** , and **OperationTimeout** parameters of the `New-PSSessionOption` cmdlet and the `$PSSessionOption` preference variable.</span></span>

- <span data-ttu-id="09763-303">Du kan också skydda fjärrdatorn genom att ange tids gräns värden program mässigt i sessionens konfiguration.</span><span class="sxs-lookup"><span data-stu-id="09763-303">You can also protect the remote computer by setting timeout values programmatically in the session configuration for the session.</span></span>

<span data-ttu-id="09763-304">När ett timeout-värde inte tillåter att en åtgärd slutförs, avslutar PowerShell åtgärden och genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="09763-304">When a timeout value does not permit a operation to complete, PowerShell terminates the operation and generates an error.</span></span>

<span data-ttu-id="09763-305">Lös felet genom att ändra kommandot till slutfört inom timeout-intervallet eller bestämma källan för tids gränsen och öka tids gränsen för att tillåta att kommandot slutförs.</span><span class="sxs-lookup"><span data-stu-id="09763-305">To resolve the error, change the command to complete within the timeout interval or determine the source of the timeout limit and increase the timeout interval to allow the command to complete.</span></span>

<span data-ttu-id="09763-306">Följande kommandon använder exempelvis `New-PSSessionOption` cmdleten för att skapa ett session-objekt med ett **OperationTimeout** -värde på 4 minuter (i MS) och använder sedan objektet session för att skapa en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="09763-306">For example, the following commands use the `New-PSSessionOption` cmdlet to create a session option object with an **OperationTimeout** value of 4 minutes (in MS) and then use the session option object to create a remote session.</span></span>

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

<span data-ttu-id="09763-307">Mer information om WS-Management timeout finns i hjälp avsnittet för WSMan-providern (typ `Get-Help WSMan` ).</span><span class="sxs-lookup"><span data-stu-id="09763-307">For more information about the WS-Management timeouts, see the Help topic for the WSMan provider (type `Get-Help WSMan`).</span></span>

<span data-ttu-id="09763-308">Mer information om `New-PSSessionOption` cmdleten finns i [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="09763-308">For more information about the `New-PSSessionOption` cmdlet, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="troubleshooting-unresponsive-behavior"></a><span data-ttu-id="09763-309">Felsöka beteende som slutar svara</span><span class="sxs-lookup"><span data-stu-id="09763-309">Troubleshooting unresponsive behavior</span></span>

<span data-ttu-id="09763-310">I det här avsnittet beskrivs fjärrstyrda problem som förhindrar att ett kommando slutförs och förhindrar eller skjuter tillbaka resultatet av PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="09763-310">This section discusses remoting problems that prevent a command from completing and prevent or delay the return of the PowerShell prompt.</span></span>

### <a name="how-to-interrupt-a-command"></a><span data-ttu-id="09763-311">Avbryta ett kommando</span><span class="sxs-lookup"><span data-stu-id="09763-311">How to interrupt a command</span></span>

<span data-ttu-id="09763-312">Vissa inbyggda Windows-program, till exempel program med ett användar gränssnitt, konsol program som efterfrågar indata och konsol program som använder Win32-konsolens API fungerar inte korrekt i PowerShell-Fjärrvärdet.</span><span class="sxs-lookup"><span data-stu-id="09763-312">Some native Windows programs, such as programs with a user interface, console applications that prompt for input, and console applications that use the Win32 console API, do not work correctly in the PowerShell remote host.</span></span>

<span data-ttu-id="09763-313">När du använder dessa program kan du se oväntade beteenden, t. ex. inga utdata, delvis utdata eller ett fjärrkommando som inte slutförs.</span><span class="sxs-lookup"><span data-stu-id="09763-313">When you use these programs, you might see unexpected behavior, such as no output, partial output, or a remote command that does not complete.</span></span>

<span data-ttu-id="09763-314">Om du vill avsluta ett program som inte svarar skriver du <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="09763-314">To end an unresponsive program, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="09763-315">Om du vill visa eventuella fel som rapporteras, skriver `$error` du in den lokala värden och fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="09763-315">To view any errors that might have been reported, type `$error` in the local host and the remote session.</span></span>

## <a name="how-to-recover-from-an-operation-failure"></a><span data-ttu-id="09763-316">Återställa från ett åtgärds fel</span><span class="sxs-lookup"><span data-stu-id="09763-316">How to recover from an operation failure</span></span>

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

<span data-ttu-id="09763-317">Det här felet returneras när en åtgärd avslutas innan den har slutförts.</span><span class="sxs-lookup"><span data-stu-id="09763-317">This error is returned when an operation is terminated before it completes.</span></span>
<span data-ttu-id="09763-318">Vanligt vis inträffar det när WinRM-tjänsten stoppar eller startar om medan andra WinRM-åtgärder pågår.</span><span class="sxs-lookup"><span data-stu-id="09763-318">Typically, it occurs when the WinRM service stops or restarts while other WinRM operations are in progress.</span></span>

<span data-ttu-id="09763-319">Lös problemet genom att kontrol lera att WinRM-tjänsten körs och försök igen.</span><span class="sxs-lookup"><span data-stu-id="09763-319">To resolve this issue, verify that the WinRM service is running and try the command again.</span></span>

1. <span data-ttu-id="09763-320">Starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="09763-320">Start PowerShell with the **Run as administrator** option.</span></span>
1. <span data-ttu-id="09763-321">Kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="09763-321">Run the following command:</span></span>

   `Start-Service WinRM`

1. <span data-ttu-id="09763-322">Kör kommandot som genererade felet igen.</span><span class="sxs-lookup"><span data-stu-id="09763-322">Re-run the command that generated the error.</span></span>

## <a name="linux-and-macos-limitations"></a><span data-ttu-id="09763-323">Begränsningar för Linux och macOS</span><span class="sxs-lookup"><span data-stu-id="09763-323">Linux and macOS limitations</span></span>

### <a name="authentication"></a><span data-ttu-id="09763-324">Autentisering</span><span class="sxs-lookup"><span data-stu-id="09763-324">Authentication</span></span>

<span data-ttu-id="09763-325">Endast grundläggande autentisering fungerar på macOS och försöker använda andra autentiseringsscheman kan leda till att processen kraschar.</span><span class="sxs-lookup"><span data-stu-id="09763-325">Only basic authentication works on macOS and attempting to use other authentication schemes may result in the process crashing.</span></span>

<span data-ttu-id="09763-326">Se anvisningarna för [OMI-autentisering](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) .</span><span class="sxs-lookup"><span data-stu-id="09763-326">Please see the [OMI authentication](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="09763-327">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="09763-327">SEE ALSO</span></span>

[<span data-ttu-id="09763-328">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="09763-328">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[<span data-ttu-id="09763-329">Exportera – PSSession</span><span class="sxs-lookup"><span data-stu-id="09763-329">Export-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[<span data-ttu-id="09763-330">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="09763-330">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="09763-331">about_Remote</span><span class="sxs-lookup"><span data-stu-id="09763-331">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="09763-332">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="09763-332">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="09763-333">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="09763-333">about_Remote_Variables</span></span>](about_Remote_Variables.md)
