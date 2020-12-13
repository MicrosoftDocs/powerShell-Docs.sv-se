---
ms.date: 08/21/2020
keywords: powershell,cmdlet
title: Kör fjärrkommandon
description: Förklarar metoder för att köra kommandon på fjärrdatorer med hjälp av PowerShell.
ms.openlocfilehash: cff18a4f51c3ed8e3ed2c1f35862a88911e7ceb5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "94391416"
---
# <a name="running-remote-commands"></a><span data-ttu-id="69e5a-104">Kör fjärrkommandon</span><span class="sxs-lookup"><span data-stu-id="69e5a-104">Running Remote Commands</span></span>

<span data-ttu-id="69e5a-105">Du kan köra kommandon på en eller flera hundra datorer med ett enda PowerShell-kommando.</span><span class="sxs-lookup"><span data-stu-id="69e5a-105">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="69e5a-106">Windows PowerShell stöder fjärrhantering med hjälp av olika tekniker, inklusive WMI, RPC och WS-Management.</span><span class="sxs-lookup"><span data-stu-id="69e5a-106">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="69e5a-107">PowerShell-kärnan stöder WMI, WS-Management och SSH-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="69e5a-107">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="69e5a-108">I PowerShell 6 stöds inte längre RPC.</span><span class="sxs-lookup"><span data-stu-id="69e5a-108">In PowerShell 6, RPC is no longer supported.</span></span> <span data-ttu-id="69e5a-109">I PowerShell 7 och senare stöds endast RPC i Windows.</span><span class="sxs-lookup"><span data-stu-id="69e5a-109">In PowerShell 7 and above, RPC is supported only in Windows.</span></span>

<span data-ttu-id="69e5a-110">Mer information om fjärr kommunikation i PowerShell Core finns i följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="69e5a-110">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="69e5a-111">[SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="69e5a-111">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="69e5a-112">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="69e5a-112">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="69e5a-113">Windows PowerShell-fjärrkommunikation utan konfiguration</span><span class="sxs-lookup"><span data-stu-id="69e5a-113">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="69e5a-114">Många Windows PowerShell-cmdlets har parametern ComputerName som gör att du kan samla in data och ändra inställningar på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="69e5a-114">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="69e5a-115">Dessa cmdletar använder varierande kommunikations protokoll och fungerar på alla Windows-operativsystem utan någon särskild konfiguration.</span><span class="sxs-lookup"><span data-stu-id="69e5a-115">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="69e5a-116">Dessa cmdlet: ar är:</span><span class="sxs-lookup"><span data-stu-id="69e5a-116">These cmdlets include:</span></span>

- [<span data-ttu-id="69e5a-117">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="69e5a-117">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="69e5a-118">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="69e5a-118">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="69e5a-119">Rensa-EventLog</span><span class="sxs-lookup"><span data-stu-id="69e5a-119">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="69e5a-120">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="69e5a-120">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="69e5a-121">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="69e5a-121">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="69e5a-122">Hämta process</span><span class="sxs-lookup"><span data-stu-id="69e5a-122">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="69e5a-123">Get-Service</span><span class="sxs-lookup"><span data-stu-id="69e5a-123">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="69e5a-124">Set-Service</span><span class="sxs-lookup"><span data-stu-id="69e5a-124">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="69e5a-125">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="69e5a-125">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="69e5a-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="69e5a-126">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="69e5a-127">Normalt är cmdletar som stöder fjärr kommunikation utan särskild konfiguration att ha parametern ComputerName och inte parametern session.</span><span class="sxs-lookup"><span data-stu-id="69e5a-127">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="69e5a-128">Om du vill hitta dessa cmdletar i din session skriver du:</span><span class="sxs-lookup"><span data-stu-id="69e5a-128">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="69e5a-129">Windows PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="69e5a-129">Windows PowerShell Remoting</span></span>

<span data-ttu-id="69e5a-130">Med hjälp av WS-Management-protokollet kan Windows PowerShell-fjärrkommunikation köra alla Windows PowerShell-kommandon på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="69e5a-130">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="69e5a-131">Du kan upprätta beständiga anslutningar, starta interaktiva sessioner och köra skript på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="69e5a-131">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="69e5a-132">Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="69e5a-132">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="69e5a-133">Mer information, inklusive instruktioner, finns i [om krav för fjärrhantering](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="69e5a-133">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="69e5a-134">När du har konfigurerat Windows PowerShell-fjärrkommunikation är många olika kommunikations strategier tillgängliga för dig.</span><span class="sxs-lookup"><span data-stu-id="69e5a-134">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="69e5a-135">I den här artikeln listas bara några av dem.</span><span class="sxs-lookup"><span data-stu-id="69e5a-135">This article lists just a few of them.</span></span> <span data-ttu-id="69e5a-136">Mer information finns i [om fjärran sluten](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="69e5a-136">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="69e5a-137">Starta en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="69e5a-137">Start an Interactive Session</span></span>

<span data-ttu-id="69e5a-138">Om du vill starta en interaktiv session med en enda fjärrdator använder du cmdleten [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .</span><span class="sxs-lookup"><span data-stu-id="69e5a-138">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span> <span data-ttu-id="69e5a-139">Om du till exempel vill starta en interaktiv session med Server01 fjärrdator skriver du:</span><span class="sxs-lookup"><span data-stu-id="69e5a-139">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="69e5a-140">Kommando tolken ändras för att visa namnet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="69e5a-140">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="69e5a-141">Alla kommandon som du skriver vid prompten körs på fjärrdatorn och resultaten visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="69e5a-141">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="69e5a-142">Om du vill avsluta den interaktiva sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="69e5a-142">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="69e5a-143">Mer information om Enter-PSSession-och Exit-PSSession-cmdlet: ar finns i:</span><span class="sxs-lookup"><span data-stu-id="69e5a-143">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="69e5a-144">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="69e5a-144">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="69e5a-145">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="69e5a-145">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="69e5a-146">Köra ett fjärrkommando</span><span class="sxs-lookup"><span data-stu-id="69e5a-146">Run a Remote Command</span></span>

<span data-ttu-id="69e5a-147">Om du vill köra ett kommando på en eller flera datorer använder du cmdleten [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="69e5a-147">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="69e5a-148">Om du till exempel vill köra kommandot [Get-värdet](/powershell/module/microsoft.powershell.utility/get-uiculture) på fjärrdatorerna Server01 och Server02, skriver du:</span><span class="sxs-lookup"><span data-stu-id="69e5a-148">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="69e5a-149">Utdata returneras till datorn.</span><span class="sxs-lookup"><span data-stu-id="69e5a-149">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="69e5a-150">Kör ett skript</span><span class="sxs-lookup"><span data-stu-id="69e5a-150">Run a Script</span></span>

<span data-ttu-id="69e5a-151">Om du vill köra ett skript på en eller flera fjärrdatorer använder du parametern sökväg för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="69e5a-151">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="69e5a-152">Skriptet måste vara på eller tillgängligt för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="69e5a-152">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="69e5a-153">Resultatet returneras till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="69e5a-153">The results are returned to your local computer.</span></span>

<span data-ttu-id="69e5a-154">Följande kommando kör till exempel DiskCollect.ps1-skriptet på fjärrdatorerna, Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="69e5a-154">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="69e5a-155">Upprätta en permanent anslutning</span><span class="sxs-lookup"><span data-stu-id="69e5a-155">Establish a Persistent Connection</span></span>

<span data-ttu-id="69e5a-156">Använd `New-PSSession` cmdleten för att skapa en beständig session på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="69e5a-156">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="69e5a-157">I följande exempel skapas fjärrsessioner på Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="69e5a-157">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="69e5a-158">Sessions-objekten lagras i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="69e5a-158">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="69e5a-159">Nu när sessionerna har upprättats kan du köra alla kommandon i dem.</span><span class="sxs-lookup"><span data-stu-id="69e5a-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="69e5a-160">Och eftersom sessionerna är permanenta kan du samla in data från ett kommando och använda det i ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="69e5a-160">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="69e5a-161">Följande kommando kör till exempel ett Get-HotFix-kommando i sessionerna i $s-variabeln och sparar resultatet i $h variabeln.</span><span class="sxs-lookup"><span data-stu-id="69e5a-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="69e5a-162">Variabeln $h skapas i varje session i $s, men den finns inte i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="69e5a-162">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="69e5a-163">Nu kan du använda data i `$h` variabeln med andra kommandon i samma session.</span><span class="sxs-lookup"><span data-stu-id="69e5a-163">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="69e5a-164">Resultaten visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="69e5a-164">The results are displayed on the local computer.</span></span> <span data-ttu-id="69e5a-165">Exempel:</span><span class="sxs-lookup"><span data-stu-id="69e5a-165">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="69e5a-166">Avancerad fjärr kommunikation</span><span class="sxs-lookup"><span data-stu-id="69e5a-166">Advanced Remoting</span></span>

<span data-ttu-id="69e5a-167">Windows PowerShell-fjärrhantering börjar bara här.</span><span class="sxs-lookup"><span data-stu-id="69e5a-167">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="69e5a-168">Genom att använda de cmdletar som installeras med Windows PowerShell kan du upprätta och konfigurera fjärrsessioner både från lokala och fjärranslutna platser, skapa anpassade och begränsade sessioner, tillåta användare att importera kommandon från en fjärrsession som faktiskt körs implicit i fjärrsessionen, konfigurera säkerheten för en fjärrsession och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="69e5a-168">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="69e5a-169">Windows PowerShell innehåller en WSMan-Provider.</span><span class="sxs-lookup"><span data-stu-id="69e5a-169">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="69e5a-170">Providern skapar en `WSMAN:` enhet som gör det möjligt att navigera i en hierarki med konfigurations inställningar på den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="69e5a-170">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="69e5a-171">Mer information om WSMan-providern finns i [WSMan-providern](/powershell/module/microsoft.wsman.management/about/about_wsman_provider) och [om WS-Management cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), eller i Windows PowerShell-konsolen skriver du `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="69e5a-171">For more information about the WSMan provider, see [WSMan Provider](/powershell/module/microsoft.wsman.management/about/about_wsman_provider) and [About WS-Management Cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="69e5a-172">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="69e5a-172">For more information, see:</span></span>

- [<span data-ttu-id="69e5a-173">Om vanliga frågor och svar om fjärr anslutning</span><span class="sxs-lookup"><span data-stu-id="69e5a-173">About Remote FAQ</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="69e5a-174">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="69e5a-174">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [<span data-ttu-id="69e5a-175">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="69e5a-175">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

<span data-ttu-id="69e5a-176">Hjälp med fjärr kommunikations fel finns i [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting).</span><span class="sxs-lookup"><span data-stu-id="69e5a-176">For help with remoting errors, see [about_Remote_Troubleshooting](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting).</span></span>

## <a name="see-also"></a><span data-ttu-id="69e5a-177">Se även</span><span class="sxs-lookup"><span data-stu-id="69e5a-177">See Also</span></span>

- [<span data-ttu-id="69e5a-178">about_Remote</span><span class="sxs-lookup"><span data-stu-id="69e5a-178">about_Remote</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="69e5a-179">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="69e5a-179">about_Remote_FAQ</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_faq)
- [<span data-ttu-id="69e5a-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="69e5a-180">about_Remote_Requirements</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
- [<span data-ttu-id="69e5a-181">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="69e5a-181">about_Remote_Troubleshooting</span></span>](/powershell/module/microsoft.powershell.core/about/about_Remote_Troubleshooting)
- [<span data-ttu-id="69e5a-182">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="69e5a-182">about_PSSessions</span></span>](/powershell/module/microsoft.powershell.core/about/about_PSSessions)
- [<span data-ttu-id="69e5a-183">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="69e5a-183">about_WS-Management_Cmdlets</span></span>](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets)
- [<span data-ttu-id="69e5a-184">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="69e5a-184">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="69e5a-185">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="69e5a-185">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)
- [<span data-ttu-id="69e5a-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="69e5a-186">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="69e5a-187">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="69e5a-187">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)
- [<span data-ttu-id="69e5a-188">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="69e5a-188">WSMan Provider</span></span>](/powershell/module/microsoft.wsman.management/about/about_wsman_provider)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
