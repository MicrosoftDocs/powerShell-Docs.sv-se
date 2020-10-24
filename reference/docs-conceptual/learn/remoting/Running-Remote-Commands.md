---
ms.date: 08/21/2020
keywords: powershell,cmdlet
title: Kör fjärrkommandon
description: Förklarar metoder för att köra kommandon på fjärrdatorer med hjälp av PowerShell.
ms.openlocfilehash: e9e07fec96cbd93d3bf06be2a1f98ec7aa7d8f19
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501362"
---
# <a name="running-remote-commands"></a><span data-ttu-id="a97de-104">Kör fjärrkommandon</span><span class="sxs-lookup"><span data-stu-id="a97de-104">Running Remote Commands</span></span>

<span data-ttu-id="a97de-105">Du kan köra kommandon på en eller flera hundra datorer med ett enda PowerShell-kommando.</span><span class="sxs-lookup"><span data-stu-id="a97de-105">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="a97de-106">Windows PowerShell stöder fjärrhantering med hjälp av olika tekniker, inklusive WMI, RPC och WS-Management.</span><span class="sxs-lookup"><span data-stu-id="a97de-106">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="a97de-107">PowerShell-kärnan stöder WMI, WS-Management och SSH-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="a97de-107">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="a97de-108">I PowerShell 6 stöds inte längre RPC.</span><span class="sxs-lookup"><span data-stu-id="a97de-108">In PowerShell 6, RPC is no longer supported.</span></span> <span data-ttu-id="a97de-109">I PowerShell 7 och senare stöds endast RPC i Windows.</span><span class="sxs-lookup"><span data-stu-id="a97de-109">In PowerShell 7 and above, RPC is supported only in Windows.</span></span>

<span data-ttu-id="a97de-110">Mer information om fjärr kommunikation i PowerShell Core finns i följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="a97de-110">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="a97de-111">[SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="a97de-111">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="a97de-112">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="a97de-112">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="a97de-113">Windows PowerShell-fjärrkommunikation utan konfiguration</span><span class="sxs-lookup"><span data-stu-id="a97de-113">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="a97de-114">Många Windows PowerShell-cmdlets har parametern ComputerName som gör att du kan samla in data och ändra inställningar på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="a97de-114">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="a97de-115">Dessa cmdletar använder varierande kommunikations protokoll och fungerar på alla Windows-operativsystem utan någon särskild konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a97de-115">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="a97de-116">Dessa cmdlet: ar är:</span><span class="sxs-lookup"><span data-stu-id="a97de-116">These cmdlets include:</span></span>

- [<span data-ttu-id="a97de-117">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="a97de-117">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="a97de-118">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="a97de-118">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="a97de-119">Rensa-EventLog</span><span class="sxs-lookup"><span data-stu-id="a97de-119">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="a97de-120">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="a97de-120">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="a97de-121">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="a97de-121">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="a97de-122">Hämta process</span><span class="sxs-lookup"><span data-stu-id="a97de-122">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="a97de-123">Get-Service</span><span class="sxs-lookup"><span data-stu-id="a97de-123">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="a97de-124">Set-Service</span><span class="sxs-lookup"><span data-stu-id="a97de-124">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="a97de-125">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="a97de-125">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="a97de-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="a97de-126">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="a97de-127">Normalt är cmdletar som stöder fjärr kommunikation utan särskild konfiguration att ha parametern ComputerName och inte parametern session.</span><span class="sxs-lookup"><span data-stu-id="a97de-127">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="a97de-128">Om du vill hitta dessa cmdletar i din session skriver du:</span><span class="sxs-lookup"><span data-stu-id="a97de-128">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="a97de-129">Windows PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="a97de-129">Windows PowerShell Remoting</span></span>

<span data-ttu-id="a97de-130">Med hjälp av WS-Management-protokollet kan Windows PowerShell-fjärrkommunikation köra alla Windows PowerShell-kommandon på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="a97de-130">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="a97de-131">Du kan upprätta beständiga anslutningar, starta interaktiva sessioner och köra skript på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="a97de-131">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="a97de-132">Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="a97de-132">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="a97de-133">Mer information, inklusive instruktioner, finns i [om krav för fjärrhantering](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="a97de-133">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="a97de-134">När du har konfigurerat Windows PowerShell-fjärrkommunikation är många olika kommunikations strategier tillgängliga för dig.</span><span class="sxs-lookup"><span data-stu-id="a97de-134">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="a97de-135">I den här artikeln listas bara några av dem.</span><span class="sxs-lookup"><span data-stu-id="a97de-135">This article lists just a few of them.</span></span> <span data-ttu-id="a97de-136">Mer information finns i [om fjärran sluten](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="a97de-136">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="a97de-137">Starta en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="a97de-137">Start an Interactive Session</span></span>

<span data-ttu-id="a97de-138">Om du vill starta en interaktiv session med en enda fjärrdator använder du cmdleten [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .</span><span class="sxs-lookup"><span data-stu-id="a97de-138">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span> <span data-ttu-id="a97de-139">Om du till exempel vill starta en interaktiv session med Server01 fjärrdator skriver du:</span><span class="sxs-lookup"><span data-stu-id="a97de-139">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="a97de-140">Kommando tolken ändras för att visa namnet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="a97de-140">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="a97de-141">Alla kommandon som du skriver vid prompten körs på fjärrdatorn och resultaten visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a97de-141">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="a97de-142">Om du vill avsluta den interaktiva sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="a97de-142">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="a97de-143">Mer information om Enter-PSSession-och Exit-PSSession-cmdlet: ar finns i:</span><span class="sxs-lookup"><span data-stu-id="a97de-143">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="a97de-144">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="a97de-144">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="a97de-145">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="a97de-145">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="a97de-146">Köra ett fjärrkommando</span><span class="sxs-lookup"><span data-stu-id="a97de-146">Run a Remote Command</span></span>

<span data-ttu-id="a97de-147">Om du vill köra ett kommando på en eller flera datorer använder du cmdleten [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="a97de-147">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="a97de-148">Om du till exempel vill köra kommandot [Get-värdet](/powershell/module/microsoft.powershell.utility/get-uiculture) på fjärrdatorerna Server01 och Server02, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a97de-148">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="a97de-149">Utdata returneras till datorn.</span><span class="sxs-lookup"><span data-stu-id="a97de-149">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="a97de-150">Kör ett skript</span><span class="sxs-lookup"><span data-stu-id="a97de-150">Run a Script</span></span>

<span data-ttu-id="a97de-151">Om du vill köra ett skript på en eller flera fjärrdatorer använder du parametern sökväg för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a97de-151">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="a97de-152">Skriptet måste vara på eller tillgängligt för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a97de-152">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="a97de-153">Resultatet returneras till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a97de-153">The results are returned to your local computer.</span></span>

<span data-ttu-id="a97de-154">Följande kommando kör till exempel DiskCollect.ps1-skriptet på fjärrdatorerna, Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="a97de-154">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="a97de-155">Upprätta en permanent anslutning</span><span class="sxs-lookup"><span data-stu-id="a97de-155">Establish a Persistent Connection</span></span>

<span data-ttu-id="a97de-156">Använd `New-PSSession` cmdleten för att skapa en beständig session på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a97de-156">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="a97de-157">I följande exempel skapas fjärrsessioner på Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="a97de-157">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="a97de-158">Sessions-objekten lagras i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a97de-158">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="a97de-159">Nu när sessionerna har upprättats kan du köra alla kommandon i dem.</span><span class="sxs-lookup"><span data-stu-id="a97de-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="a97de-160">Och eftersom sessionerna är permanenta kan du samla in data från ett kommando och använda det i ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="a97de-160">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="a97de-161">Följande kommando kör till exempel ett Get-HotFix-kommando i sessionerna i $s-variabeln och sparar resultatet i $h variabeln.</span><span class="sxs-lookup"><span data-stu-id="a97de-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="a97de-162">Variabeln $h skapas i varje session i $s, men den finns inte i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="a97de-162">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="a97de-163">Nu kan du använda data i `$h` variabeln med andra kommandon i samma session.</span><span class="sxs-lookup"><span data-stu-id="a97de-163">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="a97de-164">Resultaten visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a97de-164">The results are displayed on the local computer.</span></span> <span data-ttu-id="a97de-165">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a97de-165">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="a97de-166">Avancerad fjärr kommunikation</span><span class="sxs-lookup"><span data-stu-id="a97de-166">Advanced Remoting</span></span>

<span data-ttu-id="a97de-167">Windows PowerShell-fjärrhantering börjar bara här.</span><span class="sxs-lookup"><span data-stu-id="a97de-167">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="a97de-168">Genom att använda de cmdletar som installeras med Windows PowerShell kan du upprätta och konfigurera fjärrsessioner både från lokala och fjärranslutna platser, skapa anpassade och begränsade sessioner, tillåta användare att importera kommandon från en fjärrsession som faktiskt körs implicit i fjärrsessionen, konfigurera säkerheten för en fjärrsession och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="a97de-168">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="a97de-169">Windows PowerShell innehåller en WSMan-Provider.</span><span class="sxs-lookup"><span data-stu-id="a97de-169">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="a97de-170">Providern skapar en `WSMAN:` enhet som gör det möjligt att navigera i en hierarki med konfigurations inställningar på den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="a97de-170">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="a97de-171">Mer information om WSMan-providern finns i [WSMan-providern](https://technet.microsoft.com/library/dd819476.aspx) och [om WS-Management cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), eller i Windows PowerShell-konsolen skriver du `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="a97de-171">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="a97de-172">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="a97de-172">For more information, see:</span></span>

- [<span data-ttu-id="a97de-173">Om vanliga frågor och svar om fjärr anslutning</span><span class="sxs-lookup"><span data-stu-id="a97de-173">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="a97de-174">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a97de-174">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="a97de-175">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="a97de-175">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="a97de-176">Hjälp med fjärr kommunikations fel finns i [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="a97de-176">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="a97de-177">Se även</span><span class="sxs-lookup"><span data-stu-id="a97de-177">See Also</span></span>

- [<span data-ttu-id="a97de-178">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a97de-178">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="a97de-179">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="a97de-179">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="a97de-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="a97de-180">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="a97de-181">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="a97de-181">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="a97de-182">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="a97de-182">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="a97de-183">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a97de-183">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="a97de-184">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="a97de-184">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="a97de-185">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="a97de-185">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="a97de-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="a97de-186">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="a97de-187">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a97de-187">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="a97de-188">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="a97de-188">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
