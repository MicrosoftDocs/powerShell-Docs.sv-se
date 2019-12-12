---
ms.date: 08/14/2018
keywords: PowerShell, cmdlet
title: Kör fjärrkommandon
ms.openlocfilehash: d6609deafd8dec4f34a8412439d87dacd20d46f1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030312"
---
# <a name="running-remote-commands"></a><span data-ttu-id="8e626-103">Kör fjärrkommandon</span><span class="sxs-lookup"><span data-stu-id="8e626-103">Running Remote Commands</span></span>

<span data-ttu-id="8e626-104">Du kan köra kommandon på en eller flera hundra datorer med ett enda PowerShell-kommando.</span><span class="sxs-lookup"><span data-stu-id="8e626-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="8e626-105">Windows PowerShell stöder fjärrhantering med hjälp av olika tekniker, inklusive WMI, RPC och WS-Management.</span><span class="sxs-lookup"><span data-stu-id="8e626-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="8e626-106">PowerShell-kärnan stöder WMI, WS-Management och SSH-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="8e626-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="8e626-107">RPC stöds inte längre.</span><span class="sxs-lookup"><span data-stu-id="8e626-107">RPC is no longer supported.</span></span>

<span data-ttu-id="8e626-108">Mer information om fjärr kommunikation i PowerShell Core finns i följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="8e626-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="8e626-109">[SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="8e626-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="8e626-110">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="8e626-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="8e626-111">Windows PowerShell-fjärrkommunikation utan konfiguration</span><span class="sxs-lookup"><span data-stu-id="8e626-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="8e626-112">Många Windows PowerShell-cmdlets har parametern ComputerName som gör att du kan samla in data och ändra inställningar på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="8e626-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="8e626-113">Dessa cmdletar använder varierande kommunikations protokoll och fungerar på alla Windows-operativsystem utan någon särskild konfiguration.</span><span class="sxs-lookup"><span data-stu-id="8e626-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="8e626-114">Dessa cmdlet: ar är:</span><span class="sxs-lookup"><span data-stu-id="8e626-114">These cmdlets include:</span></span>

- [<span data-ttu-id="8e626-115">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="8e626-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="8e626-116">Testa anslutning</span><span class="sxs-lookup"><span data-stu-id="8e626-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="8e626-117">Rensa-EventLog</span><span class="sxs-lookup"><span data-stu-id="8e626-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="8e626-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="8e626-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="8e626-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="8e626-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="8e626-120">Hämta process</span><span class="sxs-lookup"><span data-stu-id="8e626-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="8e626-121">Get-service</span><span class="sxs-lookup"><span data-stu-id="8e626-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="8e626-122">Set-service</span><span class="sxs-lookup"><span data-stu-id="8e626-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="8e626-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="8e626-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="8e626-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="8e626-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="8e626-125">Normalt är cmdletar som stöder fjärr kommunikation utan särskild konfiguration att ha parametern ComputerName och inte parametern session.</span><span class="sxs-lookup"><span data-stu-id="8e626-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="8e626-126">Om du vill hitta dessa cmdletar i din session skriver du:</span><span class="sxs-lookup"><span data-stu-id="8e626-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="8e626-127">Windows PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="8e626-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="8e626-128">Med hjälp av WS-Management-protokollet kan Windows PowerShell-fjärrkommunikation köra alla Windows PowerShell-kommandon på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="8e626-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="8e626-129">Du kan upprätta beständiga anslutningar, starta interaktiva sessioner och köra skript på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="8e626-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="8e626-130">Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="8e626-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="8e626-131">Mer information, inklusive instruktioner, finns i [om krav för fjärrhantering](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="8e626-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="8e626-132">När du har konfigurerat Windows PowerShell-fjärrkommunikation är många olika kommunikations strategier tillgängliga för dig.</span><span class="sxs-lookup"><span data-stu-id="8e626-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="8e626-133">I den här artikeln listas bara några av dem.</span><span class="sxs-lookup"><span data-stu-id="8e626-133">This article lists just a few of them.</span></span> <span data-ttu-id="8e626-134">Mer information finns i [om fjärran sluten](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="8e626-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="8e626-135">Starta en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="8e626-135">Start an Interactive Session</span></span>

<span data-ttu-id="8e626-136">Om du vill starta en interaktiv session med en enda fjärrdator använder du cmdleten [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .</span><span class="sxs-lookup"><span data-stu-id="8e626-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="8e626-137">Om du till exempel vill starta en interaktiv session med Server01 fjärrdator skriver du:</span><span class="sxs-lookup"><span data-stu-id="8e626-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="8e626-138">Kommando tolken ändras för att visa namnet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8e626-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="8e626-139">Alla kommandon som du skriver vid prompten körs på fjärrdatorn och resultaten visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8e626-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="8e626-140">Om du vill avsluta den interaktiva sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="8e626-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="8e626-141">Mer information om cmdletarna Enter-PSSession och exit-PSSession finns i:</span><span class="sxs-lookup"><span data-stu-id="8e626-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="8e626-142">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="8e626-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="8e626-143">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="8e626-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="8e626-144">Köra ett fjärrkommando</span><span class="sxs-lookup"><span data-stu-id="8e626-144">Run a Remote Command</span></span>

<span data-ttu-id="8e626-145">Om du vill köra ett kommando på en eller flera datorer använder du cmdleten [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="8e626-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="8e626-146">Om du till exempel vill köra kommandot [Get-värdet](/powershell/module/microsoft.powershell.utility/get-uiculture) på fjärrdatorerna Server01 och Server02, skriver du:</span><span class="sxs-lookup"><span data-stu-id="8e626-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="8e626-147">Utdata returneras till datorn.</span><span class="sxs-lookup"><span data-stu-id="8e626-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="8e626-148">Kör ett skript</span><span class="sxs-lookup"><span data-stu-id="8e626-148">Run a Script</span></span>

<span data-ttu-id="8e626-149">Om du vill köra ett skript på en eller flera fjärrdatorer använder du parametern sökväg i `Invoke-Command`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8e626-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="8e626-150">Skriptet måste vara på eller tillgängligt för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8e626-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="8e626-151">Resultatet returneras till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8e626-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="8e626-152">Följande kommando kör till exempel skriptet DiskCollect. ps1 på fjärrdatorerna, Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="8e626-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="8e626-153">Upprätta en permanent anslutning</span><span class="sxs-lookup"><span data-stu-id="8e626-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="8e626-154">Använd `New-PSSession`-cmdlet för att skapa en beständig session på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="8e626-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="8e626-155">I följande exempel skapas fjärrsessioner på Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="8e626-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="8e626-156">Sessions-objekten lagras i `$s`-variabeln.</span><span class="sxs-lookup"><span data-stu-id="8e626-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="8e626-157">Nu när sessionerna har upprättats kan du köra alla kommandon i dem.</span><span class="sxs-lookup"><span data-stu-id="8e626-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="8e626-158">Och eftersom sessionerna är permanenta kan du samla in data från ett kommando och använda det i ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="8e626-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="8e626-159">Följande kommando kör till exempel ett Get-HotFix-kommando i sessionerna i $s-variabeln och sparar resultatet i $h-variabeln.</span><span class="sxs-lookup"><span data-stu-id="8e626-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="8e626-160">Variabeln $h skapas i varje session i $s, men den finns inte i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="8e626-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="8e626-161">Nu kan du använda data i variabeln `$h` med andra kommandon i samma session.</span><span class="sxs-lookup"><span data-stu-id="8e626-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="8e626-162">Resultaten visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8e626-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="8e626-163">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="8e626-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="8e626-164">Avancerad fjärr kommunikation</span><span class="sxs-lookup"><span data-stu-id="8e626-164">Advanced Remoting</span></span>

<span data-ttu-id="8e626-165">Windows PowerShell-fjärrhantering börjar bara här.</span><span class="sxs-lookup"><span data-stu-id="8e626-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="8e626-166">Genom att använda de cmdletar som installeras med Windows PowerShell kan du upprätta och konfigurera fjärrsessioner både från lokala och fjärranslutna platser, skapa anpassade och begränsade sessioner, tillåta användare att importera kommandon från en fjärrsession som faktiskt körs Konfigurera en fjärrsessions säkerhet på ett implicit sätt, och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="8e626-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="8e626-167">Windows PowerShell innehåller en WSMan-Provider.</span><span class="sxs-lookup"><span data-stu-id="8e626-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="8e626-168">Providern skapar en `WSMAN:` enhet som gör det möjligt att navigera genom en hierarki med konfigurations inställningar på den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="8e626-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="8e626-169">Mer information om WSMan-providern finns i [WSMan-Provider](https://technet.microsoft.com/library/dd819476.aspx) och [om WS-Management-cmdletar](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), eller i Windows PowerShell-konsolen skriver du `Get-Help wsman`.</span><span class="sxs-lookup"><span data-stu-id="8e626-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="8e626-170">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="8e626-170">For more information, see:</span></span>

- [<span data-ttu-id="8e626-171">Om vanliga frågor och svar om fjärr anslutning</span><span class="sxs-lookup"><span data-stu-id="8e626-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="8e626-172">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8e626-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="8e626-173">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="8e626-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="8e626-174">Hjälp med fjärr kommunikations fel finns i [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="8e626-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e626-175">Se även</span><span class="sxs-lookup"><span data-stu-id="8e626-175">See Also</span></span>

- [<span data-ttu-id="8e626-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8e626-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="8e626-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="8e626-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="8e626-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="8e626-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="8e626-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="8e626-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="8e626-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="8e626-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="8e626-181">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="8e626-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="8e626-182">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="8e626-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="8e626-183">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="8e626-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="8e626-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8e626-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="8e626-185">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8e626-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="8e626-186">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="8e626-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
