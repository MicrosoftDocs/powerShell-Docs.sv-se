---
ms.date: 08/14/2018
keywords: PowerShell cmdlet
title: Kör fjärrkommandon
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133840"
---
# <a name="running-remote-commands"></a><span data-ttu-id="3c35a-103">Kör fjärrkommandon</span><span class="sxs-lookup"><span data-stu-id="3c35a-103">Running Remote Commands</span></span>

<span data-ttu-id="3c35a-104">Du kan köra kommandon på en eller flera hundra datorer med ett enda PowerShell-kommando.</span><span class="sxs-lookup"><span data-stu-id="3c35a-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="3c35a-105">Windows PowerShell har stöd för fjärrhantering med hjälp av olika tekniker, inklusive WMI, RPC- och WS-Management.</span><span class="sxs-lookup"><span data-stu-id="3c35a-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="3c35a-106">PowerShell Core har stöd för WMI, WS-Management och SSH-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="3c35a-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="3c35a-107">RPC stöds inte längre.</span><span class="sxs-lookup"><span data-stu-id="3c35a-107">RPC is no longer supported.</span></span>

<span data-ttu-id="3c35a-108">Mer information om fjärrkommunikation i PowerShell Core finns i följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="3c35a-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="3c35a-109">[SSH fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="3c35a-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="3c35a-110">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="3c35a-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="3c35a-111">Windows PowerShell-fjärrkommunikation utan konfiguration</span><span class="sxs-lookup"><span data-stu-id="3c35a-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="3c35a-112">Många Windows PowerShell-cmdlets har parametern ComputerName som hjälper dig att samla in data och ändra inställningarna för en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="3c35a-113">Dessa cmdletar använder olika kommunikationsprotokoll och fungerar på alla Windows-operativsystem utan någon specialkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="3c35a-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="3c35a-114">Dessa cmdletar omfattar:</span><span class="sxs-lookup"><span data-stu-id="3c35a-114">These cmdlets include:</span></span>

- [<span data-ttu-id="3c35a-115">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="3c35a-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="3c35a-116">Testa anslutning</span><span class="sxs-lookup"><span data-stu-id="3c35a-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="3c35a-117">Rensa händelselogg</span><span class="sxs-lookup"><span data-stu-id="3c35a-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="3c35a-118">Get-händelseloggen</span><span class="sxs-lookup"><span data-stu-id="3c35a-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="3c35a-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="3c35a-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="3c35a-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="3c35a-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="3c35a-121">Get-tjänst</span><span class="sxs-lookup"><span data-stu-id="3c35a-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="3c35a-122">Set-tjänst</span><span class="sxs-lookup"><span data-stu-id="3c35a-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="3c35a-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="3c35a-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="3c35a-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="3c35a-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="3c35a-125">Normalt har parametern ComputerName cmdletar som stöder fjärrkommunikation utan särskild konfiguration och behöver inte parametern Session.</span><span class="sxs-lookup"><span data-stu-id="3c35a-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="3c35a-126">För att hitta dessa cmdletar i sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="3c35a-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="3c35a-127">Windows PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="3c35a-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="3c35a-128">Windows PowerShell-fjärrkommunikation kan med hjälp av protokollet WS-Management, du köra alla Windows PowerShell-kommandon på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="3c35a-129">Du kan fastställa beständiga anslutningar, starta interaktiva sessioner och köra skript på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="3c35a-130">Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="3c35a-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="3c35a-131">Mer information, inklusive anvisningar finns i [om Remote krav](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="3c35a-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="3c35a-132">När du har konfigurerat Windows PowerShell-fjärrkommunikation, är många strategier för fjärrkommunikation tillgängliga för dig.</span><span class="sxs-lookup"><span data-stu-id="3c35a-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="3c35a-133">Den här artikeln innehåller några av dem.</span><span class="sxs-lookup"><span data-stu-id="3c35a-133">This article lists just a few of them.</span></span> <span data-ttu-id="3c35a-134">Mer information finns i [om Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="3c35a-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="3c35a-135">Starta en interaktiv Session</span><span class="sxs-lookup"><span data-stu-id="3c35a-135">Start an Interactive Session</span></span>

<span data-ttu-id="3c35a-136">Starta en interaktiv session med en fjärransluten dator med den [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c35a-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="3c35a-137">Till exempel om du vill starta en interaktiv session med Server01 fjärrdatorn, skriver du:</span><span class="sxs-lookup"><span data-stu-id="3c35a-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="3c35a-138">Kommandotolk-ändras och visar namnet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="3c35a-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="3c35a-139">Kommandon som du anger i Kommandotolken kör på fjärrdatorn och resultatet visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3c35a-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="3c35a-140">Om du vill avsluta den interaktiva sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="3c35a-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="3c35a-141">Mer information om cmdlet: Enter-PSSession och avsluta-PSSession finns:</span><span class="sxs-lookup"><span data-stu-id="3c35a-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="3c35a-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="3c35a-143">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="3c35a-144">Kör fjärrkommandon</span><span class="sxs-lookup"><span data-stu-id="3c35a-144">Run a Remote Command</span></span>

<span data-ttu-id="3c35a-145">Om du vill köra ett kommando på en eller flera datorer, Använd den [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c35a-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="3c35a-146">Till exempel för att köra en [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) på Server01 och Server02 fjärrdatorerna, typ:</span><span class="sxs-lookup"><span data-stu-id="3c35a-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="3c35a-147">Resultatet returneras till datorn.</span><span class="sxs-lookup"><span data-stu-id="3c35a-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="3c35a-148">Köra ett skript</span><span class="sxs-lookup"><span data-stu-id="3c35a-148">Run a Script</span></span>

<span data-ttu-id="3c35a-149">Om du vill köra ett skript på en eller flera fjärrdatorer, använder du parametern FilePath för den `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c35a-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="3c35a-150">Skriptet måste infalla på eller är tillgängliga för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3c35a-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="3c35a-151">Resultaten returneras till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3c35a-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="3c35a-152">Exempelvis kör följande kommando DiskCollect.ps1 skriptet på fjärrdatorer, Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="3c35a-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="3c35a-153">Upprätta en beständig anslutning</span><span class="sxs-lookup"><span data-stu-id="3c35a-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="3c35a-154">Använd den `New-PSSession` cmdlet för att skapa en beständig session på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="3c35a-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="3c35a-155">I följande exempel skapar fjärrsessioner på Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="3c35a-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="3c35a-156">Sessionsobjekt lagras i den `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="3c35a-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="3c35a-157">Nu när sessioner upprättas, kan du köra alla kommandon i dem.</span><span class="sxs-lookup"><span data-stu-id="3c35a-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="3c35a-158">Och eftersom sessioner är beständiga kan du samla in data från ett kommando och använda det i ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="3c35a-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="3c35a-159">Till exempel följande kommando kör ett kommando för Get-HotFix i sessioner i variabeln $s och sparas resultaten i variabeln $h.</span><span class="sxs-lookup"><span data-stu-id="3c35a-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="3c35a-160">Variabeln $h skapas i varje sessioner i $s, men det finns inte i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="3c35a-161">Nu kan du använda data i den `$h` variabeln med andra kommandon i samma session.</span><span class="sxs-lookup"><span data-stu-id="3c35a-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="3c35a-162">Resultatet visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3c35a-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="3c35a-163">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="3c35a-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="3c35a-164">Avancerade fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="3c35a-164">Advanced Remoting</span></span>

<span data-ttu-id="3c35a-165">Windows PowerShell fjärrhantering bara börjar här.</span><span class="sxs-lookup"><span data-stu-id="3c35a-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="3c35a-166">Genom att använda de cmdletar som installeras med Windows PowerShell kan du etablera och konfigurera fjärrsessioner både från lokala och fjärranslutna upphör kan skapa anpassade och begränsade sessioner Tillåt användare att importera kommandon från en fjärrsession som faktiskt kör implicit på fjärrsessionen, konfigurerar du säkerheten för en fjärrsession och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="3c35a-167">Windows PowerShell innehåller en WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="3c35a-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="3c35a-168">Providern skapar en `WSMAN:` enhet som du kan gå igenom en hierarki med konfigurationsinställningarna på den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="3c35a-169">Mer information om WSMan-providern finns i [WSMan-providern](https://technet.microsoft.com/library/dd819476.aspx) och [om WS-Management-cmdletar](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), eller i Windows PowerShell-konsolen skriver `Get-Help wsman`.</span><span class="sxs-lookup"><span data-stu-id="3c35a-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="3c35a-170">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="3c35a-170">For more information, see:</span></span>

- [<span data-ttu-id="3c35a-171">Om fjärråtkomst vanliga frågor och svar</span><span class="sxs-lookup"><span data-stu-id="3c35a-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="3c35a-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c35a-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="3c35a-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="3c35a-174">Hjälp med fjärrkommunikation fel finns i [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="3c35a-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c35a-175">Se även</span><span class="sxs-lookup"><span data-stu-id="3c35a-175">See Also</span></span>

- [<span data-ttu-id="3c35a-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="3c35a-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="3c35a-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="3c35a-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="3c35a-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="3c35a-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="3c35a-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="3c35a-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="3c35a-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="3c35a-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="3c35a-181">about_WS Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="3c35a-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="3c35a-182">Anropskommandot</span><span class="sxs-lookup"><span data-stu-id="3c35a-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="3c35a-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="3c35a-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="3c35a-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c35a-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="3c35a-186">WSMan-providern</span><span class="sxs-lookup"><span data-stu-id="3c35a-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md