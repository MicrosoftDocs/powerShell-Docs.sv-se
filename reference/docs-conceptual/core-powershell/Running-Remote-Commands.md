---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Kör fjärrkommandon"
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 43f07abd642e7de235647fa151537c46ebe86cae
ms.sourcegitcommit: 6aed37d7f0c9652ae09bb8c11928da7e4783ed7f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2018
---
# <a name="running-remote-commands"></a><span data-ttu-id="308bb-103">Kör fjärrkommandon</span><span class="sxs-lookup"><span data-stu-id="308bb-103">Running Remote Commands</span></span>

<span data-ttu-id="308bb-104">Du kan köra kommandon på en eller flera hundra datorer med ett enda Windows PowerShell-kommando.</span><span class="sxs-lookup"><span data-stu-id="308bb-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="308bb-105">Windows PowerShell stöder fjärrhantering med hjälp av olika teknologier, inklusive WMI-, RPC- och WS-Management.</span><span class="sxs-lookup"><span data-stu-id="308bb-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-in-powershell-core"></a><span data-ttu-id="308bb-106">Fjärrkommunikation i PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="308bb-106">Remoting in PowerShell Core</span></span>

<span data-ttu-id="308bb-107">PowerShell Core, den nya versionen av PowerShell på Windows-, macOS- och Linux, stöder WMI, WS-Management och fjärrkommunikation med SSH.</span><span class="sxs-lookup"><span data-stu-id="308bb-107">PowerShell Core, the newer edition of PowerShell on Windows, macOS, and Linux, supports WMI, WS-Management, and SSH remoting.</span></span>
<span data-ttu-id="308bb-108">(RPC stöds inte längre.)</span><span class="sxs-lookup"><span data-stu-id="308bb-108">(RPC is no longer supported.)</span></span>

<span data-ttu-id="308bb-109">Mer information om hur du konfigurerar detta finns i:</span><span class="sxs-lookup"><span data-stu-id="308bb-109">For more information on setting this up, see:</span></span>

* <span data-ttu-id="308bb-110">[SSH fjärrkommunikation i PowerShell Core] [ssh-fjärrkommunikation]</span><span class="sxs-lookup"><span data-stu-id="308bb-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="308bb-111">[WinRM fjärrkommunikation i PowerShell Core] [winrm-fjärrkommunikation]</span><span class="sxs-lookup"><span data-stu-id="308bb-111">[WinRM Remoting in PowerShell Core][winrm-remoting]</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="308bb-112">Fjärrkommunikation utan konfiguration</span><span class="sxs-lookup"><span data-stu-id="308bb-112">Remoting Without Configuration</span></span>
<span data-ttu-id="308bb-113">Många Windows PowerShell-cmdlets har parametern ComputerName som gör det möjligt att samla in data och ändra inställningar på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="308bb-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="308bb-114">De använder olika kommunikationsteknik och många arbete på alla Windows-operativsystem som har stöd för Windows PowerShell utan någon specialkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="308bb-114">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="308bb-115">Dessa cmdletar är:</span><span class="sxs-lookup"><span data-stu-id="308bb-115">These cmdlets include:</span></span>

* [<span data-ttu-id="308bb-116">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="308bb-116">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="308bb-117">Testa anslutning</span><span class="sxs-lookup"><span data-stu-id="308bb-117">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="308bb-118">Rensa händelseloggen</span><span class="sxs-lookup"><span data-stu-id="308bb-118">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="308bb-119">Get-händelseloggen</span><span class="sxs-lookup"><span data-stu-id="308bb-119">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="308bb-120">Get-snabbkorrigering</span><span class="sxs-lookup"><span data-stu-id="308bb-120">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
* [<span data-ttu-id="308bb-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="308bb-121">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="308bb-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="308bb-122">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="308bb-123">Ange tjänst</span><span class="sxs-lookup"><span data-stu-id="308bb-123">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="308bb-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="308bb-124">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="308bb-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="308bb-125">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="308bb-126">Normalt har parametern ComputerName cmdlets som stöder fjärrkommunikation utan särskild konfiguration och har inte parametern Session.</span><span class="sxs-lookup"><span data-stu-id="308bb-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="308bb-127">Om du vill söka efter dessa cmdlets i sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="308bb-127">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="308bb-128">Windows PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="308bb-128">Windows PowerShell Remoting</span></span>
<span data-ttu-id="308bb-129">Windows PowerShell-fjärrkommunikation, som använder protokollet WS-Management, kan du köra Windows PowerShell-kommando på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="308bb-129">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="308bb-130">Gör det möjligt att upprätta beständiga anslutningar, starta 1:1 interaktiva sessioner och köra skript på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="308bb-130">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="308bb-131">Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="308bb-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="308bb-132">Mer information, inklusive instruktioner finns i [om Remote krav](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="308bb-132">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="308bb-133">När du har konfigurerat Windows PowerShell-fjärrkommunikation finns många fjärrkommunikation strategier för dig.</span><span class="sxs-lookup"><span data-stu-id="308bb-133">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="308bb-134">Resten av det här dokumentet visar några av dem.</span><span class="sxs-lookup"><span data-stu-id="308bb-134">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="308bb-135">Mer information finns i [om Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) och [om Remote vanliga frågor och svar](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="308bb-135">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="308bb-136">Starta en interaktiv Session</span><span class="sxs-lookup"><span data-stu-id="308bb-136">Start an Interactive Session</span></span>
<span data-ttu-id="308bb-137">Starta en interaktiv session med en enda fjärrdator med den [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="308bb-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="308bb-138">Skriv till exempel om du vill starta en interaktiv session med Server01 fjärrdatorn:</span><span class="sxs-lookup"><span data-stu-id="308bb-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="308bb-139">Kommandotolken ändras och visar namnet på den dator som du är ansluten.</span><span class="sxs-lookup"><span data-stu-id="308bb-139">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="308bb-140">Därefter alla kommandon som du anger i Kommandotolken kör på fjärrdatorn och resultatet visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="308bb-140">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="308bb-141">Om du vill avsluta den interaktiva sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="308bb-141">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="308bb-142">Mer information om Enter-PSSession och avsluta-PSSession cmdlets finns [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) och [avsluta-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="308bb-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="308bb-143">Kör ett kommando</span><span class="sxs-lookup"><span data-stu-id="308bb-143">Run a Remote Command</span></span>
<span data-ttu-id="308bb-144">Kör kommandon på en eller flera fjärrdatorer med den [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="308bb-144">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="308bb-145">Till exempel för att köra en [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) på Server01 och Server02 fjärrdatorerna, typ:</span><span class="sxs-lookup"><span data-stu-id="308bb-145">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="308bb-146">Resultatet returneras till din dator.</span><span class="sxs-lookup"><span data-stu-id="308bb-146">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="308bb-147">Mer information om cmdleten Invoke-Command finns [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="308bb-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="308bb-148">Köra ett skript</span><span class="sxs-lookup"><span data-stu-id="308bb-148">Run a Script</span></span>
<span data-ttu-id="308bb-149">Använd parametern FilePath för Invoke-Command-cmdlet om du vill köra ett skript på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="308bb-149">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="308bb-150">Skriptet måste vara på eller tillgänglig för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="308bb-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="308bb-151">Resultaten returneras till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="308bb-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="308bb-152">Exempelvis kör följande kommando DiskCollect.ps1 skriptet på fjärrdatorer Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="308bb-152">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="308bb-153">Mer information om cmdleten Invoke-Command finns [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="308bb-153">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="308bb-154">Upprätta en beständig anslutning</span><span class="sxs-lookup"><span data-stu-id="308bb-154">Establish a Persistent Connection</span></span>
<span data-ttu-id="308bb-155">Skapa en session på fjärrdatorn för att köra en serie relaterade kommandon som delar data, och sedan använda cmdleten Invoke-Command för att köra kommandon i sessionen som du skapar.</span><span class="sxs-lookup"><span data-stu-id="308bb-155">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="308bb-156">Använd cmdleten New-PSSession om du vill skapa en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="308bb-156">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="308bb-157">Följande kommando skapar en fjärrsession på Server01 dator och en annan fjärrsession på Server02 dator.</span><span class="sxs-lookup"><span data-stu-id="308bb-157">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="308bb-158">Session-objekt sparas i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="308bb-158">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="308bb-159">Nu när sessioner upprättas, kan du köra ett kommando i dem.</span><span class="sxs-lookup"><span data-stu-id="308bb-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="308bb-160">Och eftersom sessioner är beständiga samla in data i ett kommando och använda den i ett efterföljande kommando.</span><span class="sxs-lookup"><span data-stu-id="308bb-160">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="308bb-161">Till exempel följande kommando körs kommandot Get-snabbkorrigeringen i sessioner i variabeln $s och sparar resultatet i variabeln $h.</span><span class="sxs-lookup"><span data-stu-id="308bb-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="308bb-162">Variabeln $h skapas i alla sessioner i $s, men finns inte i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="308bb-162">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="308bb-163">Nu kan du använda informationen i variabeln $h i efterföljande kommandon, till exempel på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="308bb-163">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="308bb-164">Resultatet visas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="308bb-164">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="308bb-165">Avancerade fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="308bb-165">Advanced Remoting</span></span>
<span data-ttu-id="308bb-166">Windows PowerShell-fjärrhantering börjar bara här.</span><span class="sxs-lookup"><span data-stu-id="308bb-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="308bb-167">Med hjälp av cmdlets som installerats med Windows PowerShell kan du upprätta och konfigurera fjärrsessioner båda från lokala och fjärranslutna parterna, skapa anpassade och ej tillförlitliga sessioner, kan du importera kommandon från en fjärrsession som faktiskt kör implicit på fjärrsessionen, konfigurera säkerheten för en fjärrsession och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="308bb-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="308bb-168">För att underlätta fjärrkonfiguration inkluderar Windows PowerShell en WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="308bb-168">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="308bb-169">WSMAN: enheten som providern skapar kan du navigera i en hierarki med konfigurationsinställningarna på den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="308bb-169">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="308bb-170">Mer information om WSMan-providern finns [WSMan-providern](https://technet.microsoft.com/en-us/library/dd819476.aspx) och [om WS-Management-Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), eller ange ”Get-Help wsman” i Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="308bb-170">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="308bb-171">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="308bb-171">For more information, see:</span></span>
- [<span data-ttu-id="308bb-172">Om fjärråtkomst vanliga frågor och svar</span><span class="sxs-lookup"><span data-stu-id="308bb-172">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="308bb-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="308bb-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="308bb-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="308bb-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="308bb-175">Hjälp med fjärrkommunikation fel finns i [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="308bb-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="308bb-176">Se även</span><span class="sxs-lookup"><span data-stu-id="308bb-176">See Also</span></span>
- [<span data-ttu-id="308bb-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="308bb-177">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="308bb-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="308bb-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="308bb-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="308bb-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="308bb-180">Om fjärrfelsökning</span><span class="sxs-lookup"><span data-stu-id="308bb-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="308bb-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="308bb-181">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="308bb-182">about_WS Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="308bb-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="308bb-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="308bb-183">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="308bb-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="308bb-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="308bb-185">Ny PSSession</span><span class="sxs-lookup"><span data-stu-id="308bb-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="308bb-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="308bb-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="308bb-187">WSMan-providern</span><span class="sxs-lookup"><span data-stu-id="308bb-187">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-resmoting]: SSH-Remoting-in-PowerShell-Core.md
