---
description: Innehåller frågor och svar om att köra fjärrkommandon i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: da70a3a563031a04aeffd1ead692d9a605f14042
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271995"
---
# <a name="about-remote-faq"></a><span data-ttu-id="04e25-104">Om vanliga frågor och svar om fjärr anslutning</span><span class="sxs-lookup"><span data-stu-id="04e25-104">About Remote FAQ</span></span>

## <a name="short-description"></a><span data-ttu-id="04e25-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="04e25-105">Short description</span></span>
<span data-ttu-id="04e25-106">Innehåller frågor och svar om att köra fjärrkommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04e25-106">Contains questions and answers about running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="04e25-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="04e25-107">Long description</span></span>

<span data-ttu-id="04e25-108">När du arbetar fjärran slutet, skriver du kommandon i PowerShell på en dator (kallas "lokal dator"), men kommandona körs på en annan dator (kallas "fjärrdatorn").</span><span class="sxs-lookup"><span data-stu-id="04e25-108">When you work remotely, you type commands in PowerShell on one computer (known as the "local computer"), but the commands run on another computer (known as the "remote computer").</span></span> <span data-ttu-id="04e25-109">Upplevelsen av fjärr anslutning bör vara så mycket som att fungera direkt på fjärrdatorn som möjligt.</span><span class="sxs-lookup"><span data-stu-id="04e25-109">The experience of working remotely should be as much like working directly at the remote computer as possible.</span></span>

<span data-ttu-id="04e25-110">Obs: om du vill använda PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="04e25-110">Note: To use PowerShell remoting, the remote computer must be configured for remoting.</span></span> <span data-ttu-id="04e25-111">Mer information finns i [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e25-111">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="must-both-computers-have-powershell-installed"></a><span data-ttu-id="04e25-112">Måste båda datorerna ha PowerShell installerat?</span><span class="sxs-lookup"><span data-stu-id="04e25-112">Must both computers have PowerShell installed?</span></span>

<span data-ttu-id="04e25-113">Ja.</span><span class="sxs-lookup"><span data-stu-id="04e25-113">Yes.</span></span> <span data-ttu-id="04e25-114">För att kunna arbeta på distans måste lokala och fjärranslutna datorer ha PowerShell, Microsoft .NET Framework och protokollet för hantering av webb tjänster (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="04e25-114">To work remotely, the local and remote computers must have PowerShell, the Microsoft .NET Framework, and the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="04e25-115">Alla filer och andra resurser som behövs för att köra ett visst kommando måste finnas på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-115">Any files and other resources that are needed to execute a particular command must be on the remote computer.</span></span>

<span data-ttu-id="04e25-116">Datorer som kör Windows PowerShell 3,0 och datorer som kör Windows PowerShell 2,0 kan fjärrans luta till varandra och köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="04e25-116">Computers running Windows PowerShell 3.0 and computers running Windows PowerShell 2.0 can connect to each other remotely and run remote commands.</span></span>
<span data-ttu-id="04e25-117">Men vissa funktioner, till exempel möjligheten att koppla från en session och återansluta till den, fungerar endast när båda datorerna kör Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="04e25-117">However, some features, such as the ability to disconnect from a session and reconnect to it, work only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="04e25-118">Du måste ha behörighet att ansluta till fjärrdatorn, tillåtelse att köra PowerShell och behörighet att komma åt data lager (till exempel filer och mappar) och registret på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-118">You must have permission to connect to the remote computer, permission to run PowerShell, and permission to access data stores (such as files and folders), and the registry on the remote computer.</span></span>

<span data-ttu-id="04e25-119">Mer information finns i [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e25-119">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="how-does-remoting-work"></a><span data-ttu-id="04e25-120">Hur fungerar fjärr kommunikation?</span><span class="sxs-lookup"><span data-stu-id="04e25-120">How does remoting work?</span></span>

<span data-ttu-id="04e25-121">När du skickar ett fjärrkommando skickas kommandot över nätverket till PowerShell-motorn på fjärrdatorn och körs i PowerShell-klienten på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-121">When you submit a remote command, the command is transmitted across the network to the PowerShell engine on the remote computer, and it runs in the PowerShell client on the remote computer.</span></span> <span data-ttu-id="04e25-122">Kommando resultatet skickas tillbaka till den lokala datorn och visas i PowerShell-sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-122">The command results are sent back to the local computer and appear in the PowerShell session on the local computer.</span></span>

<span data-ttu-id="04e25-123">För att skicka kommandon och ta emot utdata använder PowerShell WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="04e25-123">To transmit the commands and receive the output, PowerShell uses the WS-Management protocol.</span></span> <span data-ttu-id="04e25-124">Information om WS-Management-protokollet finns i [WS-Management-protokollet](/windows/win32/winrm/ws-management-protocol) i Windows-dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="04e25-124">For information about the WS-Management protocol, see [WS-Management Protocol](/windows/win32/winrm/ws-management-protocol) in the Windows documentation.</span></span>

<span data-ttu-id="04e25-125">Från och med Windows PowerShell 3,0 lagras fjärrsessioner på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-125">Beginning in Windows PowerShell 3.0, remote sessions are stored on the remote computer.</span></span> <span data-ttu-id="04e25-126">På så sätt kan du koppla från sessionen och återansluta från en annan session eller en annan dator utan att avbryta kommandona eller förlora tillstånd.</span><span class="sxs-lookup"><span data-stu-id="04e25-126">This enables you to disconnect from the session and reconnect from a different session or a different computer without interrupting the commands or losing state.</span></span>

### <a name="is-powershell-remoting-secure"></a><span data-ttu-id="04e25-127">Är PowerShell-fjärrkommunikation säker?</span><span class="sxs-lookup"><span data-stu-id="04e25-127">Is PowerShell remoting secure?</span></span>

<span data-ttu-id="04e25-128">När du ansluter till en fjärrdator använder systemet användar namn och lösen ord för att logga in på den lokala datorn eller de autentiseringsuppgifter som du anger i kommandot för att logga in dig på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-128">When you connect to a remote computer, the system uses the username and password credentials on the local computer or the credentials that you supply in the command to log you in to the remote computer.</span></span> <span data-ttu-id="04e25-129">Autentiseringsuppgifterna och resten av överföringen är krypterade.</span><span class="sxs-lookup"><span data-stu-id="04e25-129">The credentials and the rest of the transmission are encrypted.</span></span>

<span data-ttu-id="04e25-130">Om du vill lägga till ytterligare skydd kan du konfigurera fjärrdatorn att använda Secure Sockets Layer (SSL) i stället för HTTP för att lyssna efter WinRM-begäranden (Windows Remote Management).</span><span class="sxs-lookup"><span data-stu-id="04e25-130">To add additional protection, you can configure the remote computer to use Secure Sockets Layer (SSL) instead of HTTP to listen for Windows Remote Management (WinRM) requests.</span></span> <span data-ttu-id="04e25-131">Sedan kan användarna använda parametern **UseSSL** i `Invoke-Command` `New-PSSession` cmdletarna, och för att `Enter-PSSession` upprätta en anslutning.</span><span class="sxs-lookup"><span data-stu-id="04e25-131">Then, users can use the **UseSSL** parameter of the `Invoke-Command`, `New-PSSession`, and `Enter-PSSession` cmdlets when establishing a connection.</span></span> <span data-ttu-id="04e25-132">Det här alternativet använder den säkrare HTTPS-kanalen i stället för HTTP.</span><span class="sxs-lookup"><span data-stu-id="04e25-132">This option uses the more secure HTTPS channel instead of HTTP.</span></span>

### <a name="do-all-remote-commands-require-powershell-remoting"></a><span data-ttu-id="04e25-133">Kräver alla fjärrkommandon PowerShell-fjärrkommunikation?</span><span class="sxs-lookup"><span data-stu-id="04e25-133">Do all remote commands require PowerShell remoting?</span></span>

<span data-ttu-id="04e25-134">Nej.</span><span class="sxs-lookup"><span data-stu-id="04e25-134">No.</span></span> <span data-ttu-id="04e25-135">Flera cmdlets har en **computername** -parameter som låter dig hämta objekt från fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-135">Several cmdlets have a **ComputerName** parameter that lets you get objects from the remote computer.</span></span>

<span data-ttu-id="04e25-136">Dessa cmdletar använder inte PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="04e25-136">These cmdlets do not use PowerShell remoting.</span></span> <span data-ttu-id="04e25-137">Så du kan använda dem på alla datorer som kör PowerShell, även om datorn inte har kon figurer ATS för PowerShell-fjärrkommunikation eller om datorn inte uppfyller kraven för PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="04e25-137">So, you can use them on any computer that is running PowerShell, even if the computer is not configured for PowerShell remoting or if the computer does not meet the requirements for PowerShell remoting.</span></span>

<span data-ttu-id="04e25-138">Dessa cmdletar innehåller följande:</span><span class="sxs-lookup"><span data-stu-id="04e25-138">These cmdlets include the following:</span></span>

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

<span data-ttu-id="04e25-139">Om du vill hitta alla cmdletar med parametern **computername** skriver du:</span><span class="sxs-lookup"><span data-stu-id="04e25-139">To find all the cmdlets with a **ComputerName** parameter, type:</span></span>

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

<span data-ttu-id="04e25-140">För att avgöra om parametern **computername** för en viss cmdlet kräver PowerShell-fjärrkommunikation, se parameter beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="04e25-140">To determine whether the **ComputerName** parameter of a particular cmdlet requires PowerShell remoting, see the parameter description.</span></span> <span data-ttu-id="04e25-141">Om du vill visa parameter beskrivningen skriver du:</span><span class="sxs-lookup"><span data-stu-id="04e25-141">To display the parameter description, type:</span></span>

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

<span data-ttu-id="04e25-142">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="04e25-142">For example:</span></span>

```powershell
Get-Help Get-Process -Parameter ComputerName
```

<span data-ttu-id="04e25-143">Använd cmdleten för alla andra kommandon `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="04e25-143">For all other commands, use the `Invoke-Command` cmdlet.</span></span>

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a><span data-ttu-id="04e25-144">Hur gör jag för att du köra ett kommando på en fjärrdator?</span><span class="sxs-lookup"><span data-stu-id="04e25-144">How do I run a command on a remote computer?</span></span>

<span data-ttu-id="04e25-145">Använd cmdleten om du vill köra ett kommando på en fjärrdator `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="04e25-145">To run a command on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="04e25-146">Sätt ditt kommando i klammerparenteser ( `{}` ) för att göra det till ett skript block.</span><span class="sxs-lookup"><span data-stu-id="04e25-146">Enclose your command in braces (`{}`) to make it a script block.</span></span> <span data-ttu-id="04e25-147">Använd parametern **script block** för `Invoke-Command` för att ange kommandot.</span><span class="sxs-lookup"><span data-stu-id="04e25-147">Use the **ScriptBlock** parameter of `Invoke-Command` to specify the command.</span></span>

<span data-ttu-id="04e25-148">Du kan använda parametern **computername** för `Invoke-Command` för att ange en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="04e25-148">You can use the **ComputerName** parameter of `Invoke-Command` to specify a remote computer.</span></span> <span data-ttu-id="04e25-149">Du kan också skapa en permanent anslutning till en fjärrdator (en session) och sedan använda parametern **session** för `Invoke-Command` att köra kommandot i sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-149">Or, you can create a persistent connection to a remote computer (a session) and then use the **Session** parameter of `Invoke-Command` to run the command in the session.</span></span>

<span data-ttu-id="04e25-150">Följande kommandon kör till exempel ett- `Get-Process` kommando via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="04e25-150">For example, the following commands run a `Get-Process` command remotely.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

<span data-ttu-id="04e25-151">Om du vill avbryta ett fjärrkommando skriver du <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="04e25-151">To interrupt a remote command, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="04e25-152">Avbrotts förfrågan skickas till fjärrdatorn, där den avslutar fjärrkommandot.</span><span class="sxs-lookup"><span data-stu-id="04e25-152">The interruption request is passed to the remote computer, where it terminates the remote command.</span></span>

<span data-ttu-id="04e25-153">Mer information om fjärrkommandon finns i about_Remote och hjälp avsnitten för de cmdletar som stöder fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="04e25-153">For more information about remote commands, see about_Remote and the Help topics for the cmdlets that support remoting.</span></span>

### <a name="can-i-just-telnet-into-a-remote-computer"></a><span data-ttu-id="04e25-154">Kan jag bara Telnet till en fjärrdator?</span><span class="sxs-lookup"><span data-stu-id="04e25-154">Can I just telnet into a remote computer?</span></span>

<span data-ttu-id="04e25-155">Du kan använda `Enter-PSSession` cmdleten för att starta en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="04e25-155">You can use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="04e25-156">I PowerShell-prompten skriver du:</span><span class="sxs-lookup"><span data-stu-id="04e25-156">At the PowerShell prompt, type:</span></span>

```powershell
Enter-PSSession <ComputerName>
```

<span data-ttu-id="04e25-157">Kommando tolken ändras för att visa att du är ansluten till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-157">The command prompt changes to show that you are connected to the remote computer.</span></span>

```
<ComputerName>\C:>
```

<span data-ttu-id="04e25-158">Nu kan de kommandon som du skriver köra på fjärrdatorn precis som om du skrev dem direkt på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-158">Now, the commands that you type run on the remote computer just as though you typed them directly on the remote computer.</span></span>

<span data-ttu-id="04e25-159">Om du vill avsluta den interaktiva sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="04e25-159">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="04e25-160">En interaktiv session är en beständig session som använder WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="04e25-160">An interactive session is a persistent session that uses the WS-Management protocol.</span></span> <span data-ttu-id="04e25-161">Det är inte samma sak som att använda Telnet, men det ger samma upplevelse.</span><span class="sxs-lookup"><span data-stu-id="04e25-161">It is not the same as using Telnet, but it provides a similar experience.</span></span>

<span data-ttu-id="04e25-162">Mer information finns i `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="04e25-162">For more information, see `Enter-PSSession`.</span></span>

### <a name="can-i-create-a-persistent-connection"></a><span data-ttu-id="04e25-163">Kan jag skapa en permanent anslutning?</span><span class="sxs-lookup"><span data-stu-id="04e25-163">Can I create a persistent connection?</span></span>

<span data-ttu-id="04e25-164">Ja.</span><span class="sxs-lookup"><span data-stu-id="04e25-164">Yes.</span></span> <span data-ttu-id="04e25-165">Du kan köra fjärrkommandon genom att ange namnet på fjärrdatorn, dess NetBIOS-namn eller dess IP-adress.</span><span class="sxs-lookup"><span data-stu-id="04e25-165">You can run remote commands by specifying the name of the remote computer, its NetBIOS name, or its IP address.</span></span> <span data-ttu-id="04e25-166">Du kan också köra fjärrkommandon genom att ange en PowerShell-session (PSSession) som är ansluten till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-166">Or, you can run remote commands by specifying a PowerShell session (PSSession) that is connected to the remote computer.</span></span>

<span data-ttu-id="04e25-167">När du använder parametern **computername** för `Invoke-Command` eller `Enter-PSSession` , upprättar PowerShell en tillfällig anslutning.</span><span class="sxs-lookup"><span data-stu-id="04e25-167">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, PowerShell establishes a temporary connection.</span></span> <span data-ttu-id="04e25-168">PowerShell använder anslutningen för att bara köra det aktuella kommandot och sedan stängs anslutningen.</span><span class="sxs-lookup"><span data-stu-id="04e25-168">PowerShell uses the connection to run only the current command, and then it closes the connection.</span></span> <span data-ttu-id="04e25-169">Det här är en mycket effektiv metod för att köra ett enda kommando eller flera orelaterade kommandon, även på många fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="04e25-169">This is a very efficient method for running a single command or several unrelated commands, even on many remote computers.</span></span>

<span data-ttu-id="04e25-170">När du använder `New-PSSession` cmdleten för att skapa en PSSession upprättar PowerShell en permanent anslutning för PSSession.</span><span class="sxs-lookup"><span data-stu-id="04e25-170">When you use the `New-PSSession` cmdlet to create a PSSession, PowerShell establishes a persistent connection for the PSSession.</span></span> <span data-ttu-id="04e25-171">Sedan kan du köra flera kommandon i PSSession, inklusive kommandon som delar data.</span><span class="sxs-lookup"><span data-stu-id="04e25-171">Then, you can run multiple commands in the PSSession, including commands that share data.</span></span>

<span data-ttu-id="04e25-172">Normalt skapar du en PSSession för att köra en serie relaterade kommandon som delar data.</span><span class="sxs-lookup"><span data-stu-id="04e25-172">Typically, you create a PSSession to run a series of related commands that share data.</span></span> <span data-ttu-id="04e25-173">Annars räcker den tillfälliga anslutningen som skapas av parametern **computername** för de flesta kommandon.</span><span class="sxs-lookup"><span data-stu-id="04e25-173">Otherwise, the temporary connection created by the **ComputerName** parameter is sufficient for most commands.</span></span>

<span data-ttu-id="04e25-174">Mer information om sessioner finns about_PSSessions.</span><span class="sxs-lookup"><span data-stu-id="04e25-174">For more information about sessions, see about_PSSessions.</span></span>

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a><span data-ttu-id="04e25-175">Kan jag köra kommandon på fler än en dator åt gången?</span><span class="sxs-lookup"><span data-stu-id="04e25-175">Can I run commands on more than one computer at a time?</span></span>

<span data-ttu-id="04e25-176">Ja.</span><span class="sxs-lookup"><span data-stu-id="04e25-176">Yes.</span></span> <span data-ttu-id="04e25-177">Parametern **computername** för `Invoke-Command` cmdleten accepterar flera dator namn och parametern **session** accepterar flera PSSessions.</span><span class="sxs-lookup"><span data-stu-id="04e25-177">The **ComputerName** parameter of the `Invoke-Command` cmdlet accepts multiple computer names, and the **Session** parameter accepts multiple PSSessions.</span></span>

<span data-ttu-id="04e25-178">När du kör ett `Invoke-Command` kommando kör PowerShell kommandona på alla angivna datorer eller i alla angivna PSSessions.</span><span class="sxs-lookup"><span data-stu-id="04e25-178">When you run an `Invoke-Command` command, PowerShell runs the commands on all of the specified computers or in all of the specified PSSessions.</span></span>

<span data-ttu-id="04e25-179">PowerShell kan hantera hundratals samtidiga fjärr anslutningar.</span><span class="sxs-lookup"><span data-stu-id="04e25-179">PowerShell can manage hundreds of concurrent remote connections.</span></span> <span data-ttu-id="04e25-180">Antalet fjärrkommandon som du kan skicka kan dock begränsas av resurserna på din dator och dess kapacitet att upprätta och underhålla flera nätverks anslutningar.</span><span class="sxs-lookup"><span data-stu-id="04e25-180">However, the number of remote commands that you can send might be limited by the resources of your computer and its capacity to establish and maintain multiple network connections.</span></span>

<span data-ttu-id="04e25-181">Mer information finns i exemplet i `Invoke-Command` Hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="04e25-181">For more information, see the example in the `Invoke-Command` Help topic.</span></span>

### <a name="where-are-my-profiles"></a><span data-ttu-id="04e25-182">Var finns mina profiler?</span><span class="sxs-lookup"><span data-stu-id="04e25-182">Where are my profiles?</span></span>

<span data-ttu-id="04e25-183">PowerShell-profiler körs inte automatiskt i fjärrsessioner, så de kommandon som profilen lägger till finns inte i sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-183">PowerShell profiles are not run automatically in remote sessions, so the commands that the profile adds are not present in the session.</span></span> <span data-ttu-id="04e25-184">Dessutom `$profile` är den automatiska variabeln inte ifylld i fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="04e25-184">In addition, the `$profile` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="04e25-185">Använd cmdleten för att köra en profil i en session `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="04e25-185">To run a profile in a session, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="04e25-186">Följande kommando kör till exempel CurrentUserCurrentHost-profilen från den lokala datorn i sessionen i `$s` .</span><span class="sxs-lookup"><span data-stu-id="04e25-186">For example, the following command runs the CurrentUserCurrentHost profile from the local computer in the session in `$s`.</span></span>

```
Invoke-Command -Session $s -FilePath $profile
```

<span data-ttu-id="04e25-187">Följande kommando kör CurrentUserCurrentHost-profilen från fjärrdatorn i sessionen i `$s` .</span><span class="sxs-lookup"><span data-stu-id="04e25-187">The following command runs the CurrentUserCurrentHost profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="04e25-188">Eftersom `$profile` variabeln inte är ifylld använder kommandot den explicita sökvägen till profilen.</span><span class="sxs-lookup"><span data-stu-id="04e25-188">Because the `$profile` variable is not populated, the command uses the explicit path to the profile.</span></span>

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="04e25-189">När du har kört det här kommandot är de kommandon som profilen lägger till i sessionen tillgängliga i `$s` .</span><span class="sxs-lookup"><span data-stu-id="04e25-189">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

<span data-ttu-id="04e25-190">Du kan också använda ett start skript i en sessionshantering för att köra en profil i varje fjärrsession som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-190">You can also use a startup script in a session configuration to run a profile in every remote session that uses the session configuration.</span></span>

<span data-ttu-id="04e25-191">Mer information om PowerShell-profiler finns about_Profiles.</span><span class="sxs-lookup"><span data-stu-id="04e25-191">For more information about PowerShell profiles, see about_Profiles.</span></span>
<span data-ttu-id="04e25-192">Mer information om sessionsdata finns i `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="04e25-192">For more information about session configurations, see `Register-PSSessionConfiguration`.</span></span>

### <a name="how-does-throttling-work-on-remote-commands"></a><span data-ttu-id="04e25-193">Hur fungerar begränsningen på fjärrkommandona?</span><span class="sxs-lookup"><span data-stu-id="04e25-193">How does throttling work on remote commands?</span></span>

<span data-ttu-id="04e25-194">För att hjälpa dig att hantera resurserna på den lokala datorn innehåller PowerShell en funktion för begränsning av varje kommando som gör att du kan begränsa antalet samtidiga fjärr anslutningar som upprättas för varje kommando.</span><span class="sxs-lookup"><span data-stu-id="04e25-194">To help you manage the resources on your local computer, PowerShell includes a per-command throttling feature that lets you limit the number of concurrent remote connections that are established for each command.</span></span>

<span data-ttu-id="04e25-195">Standardvärdet är 32 samtidiga anslutningar, men du kan använda parametern **ThrottleLimit** för cmdletarna för att ange en anpassad begränsnings gräns för vissa kommandon.</span><span class="sxs-lookup"><span data-stu-id="04e25-195">The default is 32 concurrent connections, but you can use the **ThrottleLimit** parameter of the cmdlets to set a custom throttle limit for particular commands.</span></span>

<span data-ttu-id="04e25-196">När du använder begränsnings funktionen måste du komma ihåg att den tillämpas på varje kommando, inte i hela sessionen eller på datorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-196">When you use the throttling feature, remember that it is applied to each command, not to the entire session or to the computer.</span></span> <span data-ttu-id="04e25-197">Om du kör kommandon samtidigt i flera sessioner eller PSSessions är antalet samtidiga anslutningar summan av samtidiga anslutningar i alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="04e25-197">If you are running commands concurrently in several sessions or PSSessions, the number of concurrent connections is the sum of the concurrent connections in all the sessions.</span></span>

<span data-ttu-id="04e25-198">Om du vill hitta cmdletar med en **ThrottleLimit** -parameter skriver du:</span><span class="sxs-lookup"><span data-stu-id="04e25-198">To find cmdlets with a **ThrottleLimit** parameter, type:</span></span>

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a><span data-ttu-id="04e25-199">Skiljer sig utdata från fjärrkommandon från lokala utdata?</span><span class="sxs-lookup"><span data-stu-id="04e25-199">Is the output of remote commands different from local output?</span></span>

<span data-ttu-id="04e25-200">När du använder PowerShell lokalt kan du skicka och ta emot "Live" .NET Framework objekt; "Live"-objekt är objekt som är associerade med faktiska program eller system komponenter.</span><span class="sxs-lookup"><span data-stu-id="04e25-200">When you use PowerShell locally, you send and receive "live" .NET Framework objects; "live" objects are objects that are associated with actual programs or system components.</span></span> <span data-ttu-id="04e25-201">När du anropar metoderna eller ändrar egenskaperna för Live-objekt påverkar ändringarna det faktiska programmet eller den aktuella komponenten.</span><span class="sxs-lookup"><span data-stu-id="04e25-201">When you invoke the methods or change the properties of live objects, the changes affect the actual program or component.</span></span> <span data-ttu-id="04e25-202">När egenskaperna för ett program eller en komponent ändras, ändras även egenskaperna för objektet som representerar dem.</span><span class="sxs-lookup"><span data-stu-id="04e25-202">And, when the properties of a program or component change, the properties of the object that represent them also change.</span></span>

<span data-ttu-id="04e25-203">Men eftersom de flesta Live-objekt inte kan överföras via nätverket, serialiserar PowerShell "de flesta objekt som skickas i fjärrkommandon, det vill säga varje objekt till en serie med XML (begränsnings språk i XML [CLiXML]) data element för överföring.</span><span class="sxs-lookup"><span data-stu-id="04e25-203">However, because most live objects cannot be transmitted over the network, PowerShell "serializes" most of the objects sent in remote commands, that is, it converts each object into a series of XML (Constraint Language in XML [CLiXML]) data elements for transmission.</span></span>

<span data-ttu-id="04e25-204">När PowerShell tar emot ett serialiserat objekt, konverterar det XML till en avserialiserad objekt typ.</span><span class="sxs-lookup"><span data-stu-id="04e25-204">When PowerShell receives a serialized object, it converts the XML into a deserialized object type.</span></span> <span data-ttu-id="04e25-205">Det avserialiserade objektet är en korrekt post för programmets eller komponentens egenskaper vid en tidigare tidpunkt, men är inte längre "Live", det vill säga att det inte längre är direkt kopplat till komponenten.</span><span class="sxs-lookup"><span data-stu-id="04e25-205">The deserialized object is an accurate record of the properties of the program or component at a previous time, but it is no longer "live", that is, it is no longer directly associated with the component.</span></span> <span data-ttu-id="04e25-206">Och metoderna tas bort eftersom de inte längre gäller.</span><span class="sxs-lookup"><span data-stu-id="04e25-206">And, the methods are removed because they are no longer effective.</span></span>

<span data-ttu-id="04e25-207">Normalt kan du använda avserialiserade objekt på samma sätt som du använder Live-objekt, men du måste vara medveten om deras begränsningar.</span><span class="sxs-lookup"><span data-stu-id="04e25-207">Typically, you can use deserialized objects just as you would use live objects, but you must be aware of their limitations.</span></span> <span data-ttu-id="04e25-208">Dessutom har de objekt som returneras av cmdlet: en `Invoke-Command` Ytterligare egenskaper som hjälper dig att fastställa kommandots ursprung.</span><span class="sxs-lookup"><span data-stu-id="04e25-208">Also, the objects that are returned by the `Invoke-Command` cmdlet have additional properties that help you to determine the origin of the command.</span></span>

<span data-ttu-id="04e25-209">Vissa objekt typer, till exempel DirectoryInfo-objekt och GUID, konverteras tillbaka till aktiva objekt när de tas emot.</span><span class="sxs-lookup"><span data-stu-id="04e25-209">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="04e25-210">Dessa objekt behöver inte någon särskild hantering eller formatering.</span><span class="sxs-lookup"><span data-stu-id="04e25-210">These objects do not need any special handling or formatting.</span></span>

<span data-ttu-id="04e25-211">Information om hur du tolkar och formaterar fjärrutdata finns i [about_Remote_Output](about_Remote_Output.md).</span><span class="sxs-lookup"><span data-stu-id="04e25-211">For information about interpreting and formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

### <a name="can-i-run-background-jobs-remotely"></a><span data-ttu-id="04e25-212">Kan jag köra bakgrunds jobb på distans?</span><span class="sxs-lookup"><span data-stu-id="04e25-212">Can I run background jobs remotely?</span></span>

<span data-ttu-id="04e25-213">Ja.</span><span class="sxs-lookup"><span data-stu-id="04e25-213">Yes.</span></span> <span data-ttu-id="04e25-214">Ett PowerShell-bakgrunds jobb är ett PowerShell-kommando som körs asynkront utan att samverka med sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-214">A PowerShell background job is a PowerShell command that runs asynchronously without interacting with the session.</span></span> <span data-ttu-id="04e25-215">När du startar ett bakgrunds jobb returnerar kommando tolken omedelbart och du kan fortsätta att arbeta i sessionen medan jobbet körs även om det körs under en längre tid.</span><span class="sxs-lookup"><span data-stu-id="04e25-215">When you start a background job, the command prompt returns immediately, and you can continue to work in the session while the job runs even if it runs for an extended period of time.</span></span>

<span data-ttu-id="04e25-216">Du kan starta ett bakgrunds jobb även om andra kommandon körs eftersom bakgrunds jobb alltid körs asynkront i en tillfällig session.</span><span class="sxs-lookup"><span data-stu-id="04e25-216">You can start a background job even while other commands are running because background jobs always run asynchronously in a temporary session.</span></span>

<span data-ttu-id="04e25-217">Du kan köra bakgrunds jobb på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="04e25-217">You can run background jobs on a local or remote computer.</span></span> <span data-ttu-id="04e25-218">Som standard körs ett bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-218">By default, a background job runs on the local computer.</span></span> <span data-ttu-id="04e25-219">Du kan dock använda **AsJob** -parametern för `Invoke-Command` cmdleten för att köra ett fjärrkommando som bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="04e25-219">However, you can use the **AsJob** parameter of the `Invoke-Command` cmdlet to run any remote command as a background job.</span></span> <span data-ttu-id="04e25-220">Du kan också använda `Invoke-Command` för att köra ett `Start-Job` kommando via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="04e25-220">And, you can use `Invoke-Command` to run a `Start-Job` command remotely.</span></span>

<span data-ttu-id="04e25-221">Mer information om bakgrunds jobb i PowerShell finns i [about_Jobs (about_Jobs. MD)] och [about_Remote_Jobs (about_Remote_Jobs. MD)].</span><span class="sxs-lookup"><span data-stu-id="04e25-221">For more information about background jobs in PowerShell , see [about_Jobs(about_Jobs.md)] and [about_Remote_Jobs(about_Remote_Jobs.md)].</span></span>

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a><span data-ttu-id="04e25-222">Kan jag köra Windows-program på en fjärran sluten dator?</span><span class="sxs-lookup"><span data-stu-id="04e25-222">Can I run windows programs on a remote computer?</span></span>

<span data-ttu-id="04e25-223">Du kan använda PowerShell-fjärrkommandon för att köra Windows-baserade program på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="04e25-223">You can use PowerShell remote commands to run Windows-based programs on remote computers.</span></span> <span data-ttu-id="04e25-224">Du kan till exempel köra `Shutdown.exe` eller `Ipconfig.exe` på en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="04e25-224">For example, you can run `Shutdown.exe` or `Ipconfig.exe` on a remote computer.</span></span>

<span data-ttu-id="04e25-225">Du kan dock inte använda PowerShell-kommandon för att öppna användar gränssnittet för alla program på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="04e25-225">However, you cannot use PowerShell commands to open the user interface for any program on a remote computer.</span></span>

<span data-ttu-id="04e25-226">När du startar ett Windows-program på en fjärrdator slutförs inte kommandot och kommando tolken i PowerShell returnerar inte förrän programmet är klart eller tills du trycker på <kbd>CTRL</kbd> + <kbd>C</kbd> för att avbryta kommandot.</span><span class="sxs-lookup"><span data-stu-id="04e25-226">When you start a Windows program on a remote computer, the command is not completed, and the PowerShell command prompt does not return, until the program is finished or until you press <kbd>CTRL</kbd>+<kbd>C</kbd> to interrupt the command.</span></span> <span data-ttu-id="04e25-227">Om du till exempel kör `Ipconfig.exe` programmet på en fjärrdator returneras inte kommando tolken förrän `Ipconfig.exe` har slutförts.</span><span class="sxs-lookup"><span data-stu-id="04e25-227">For example, if you run the `Ipconfig.exe` program on a remote computer, the command prompt does not return until `Ipconfig.exe` is completed.</span></span>

<span data-ttu-id="04e25-228">Om du använder fjärrkommandon för att starta ett program som har ett användar gränssnitt startar program processen, men användar gränssnittet visas inte.</span><span class="sxs-lookup"><span data-stu-id="04e25-228">If you use remote commands to start a program that has a user interface, the program process starts, but the user interface does not appear.</span></span> <span data-ttu-id="04e25-229">PowerShell-kommandot slutförs inte och kommando tolken returneras inte förrän du stoppar program processen eller tills du trycker på <kbd>CTRL</kbd> + <kbd>C</kbd>, som avbryter kommandot och stoppar processen.</span><span class="sxs-lookup"><span data-stu-id="04e25-229">The PowerShell command is not completed, and the command prompt does not return until you stop the program process or until you press <kbd>CTRL</kbd>+<kbd>C</kbd>, which interrupts the command and stops the process.</span></span>

<span data-ttu-id="04e25-230">Om du till exempel använder ett PowerShell-kommando för att köra `Notepad` på en fjärrdator, startar anteckningar-processen på fjärrdatorn, men användar gränssnittet i anteckningar visas inte.</span><span class="sxs-lookup"><span data-stu-id="04e25-230">For example, if you use a PowerShell command to run `Notepad` on a remote computer, the Notepad process starts on the remote computer, but the Notepad user interface does not appear.</span></span> <span data-ttu-id="04e25-231">Tryck på <kbd>CTRL</kbd>C om du vill avbryta kommandot och återställa kommando tolken + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="04e25-231">To interrupt the command and restore the command prompt, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a><span data-ttu-id="04e25-232">Kan jag begränsa de kommandon som användarna kan köra via fjärr anslutning på datorn?</span><span class="sxs-lookup"><span data-stu-id="04e25-232">Can I limit the commands that users can run remotely on my computer?</span></span>

<span data-ttu-id="04e25-233">Ja.</span><span class="sxs-lookup"><span data-stu-id="04e25-233">Yes.</span></span> <span data-ttu-id="04e25-234">Varje fjärran sluten session måste använda en av sessionens konfigurationer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-234">Every remote session must use one of the session configurations on the remote computer.</span></span> <span data-ttu-id="04e25-235">Du kan hantera sessionsinställningar på din dator (och behörigheterna för dessa sessioner) för att fastställa vem som kan köra kommandon på en annan dator och vilka kommandon de kan köra.</span><span class="sxs-lookup"><span data-stu-id="04e25-235">You can manage the session configurations on your computer (and the permissions to those session configurations) to determine who can run commands remotely on your computer and which commands they can run.</span></span>

<span data-ttu-id="04e25-236">En konfiguration av sessionen konfigurerar miljön för sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-236">A session configuration configures the environment for the session.</span></span> <span data-ttu-id="04e25-237">Du kan definiera konfigurationen genom att använda en sammansättning som implementerar en ny konfigurations klass eller genom att använda ett skript som körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-237">You can define the configuration by using an assembly that implements a new configuration class or by using a script that runs in the session.</span></span> <span data-ttu-id="04e25-238">Konfigurationen kan avgöra vilka kommandon som är tillgängliga i sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-238">The configuration can determine the commands that are available in the session.</span></span>
<span data-ttu-id="04e25-239">Konfigurationen kan dessutom innehålla inställningar som skyddar datorn, till exempel inställningar som begränsar mängden data som sessionen kan ta emot via fjärr anslutning i ett enda objekt eller kommando.</span><span class="sxs-lookup"><span data-stu-id="04e25-239">And, the configuration can include settings that protect the computer, such as settings that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="04e25-240">Du kan också ange en säkerhets beskrivning som avgör vilka behörigheter som krävs för att använda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="04e25-240">You can also specify a security descriptor that determines the permissions that are required to use the configuration.</span></span>

<span data-ttu-id="04e25-241">`Enable-PSRemoting`Cmdleten skapar standardkonfigurationerna för sessioner på datorn: Microsoft. PowerShell, Microsoft. PowerShell. Workflow och Microsoft. PowerShell32 (endast 64-bitars operativ system).</span><span class="sxs-lookup"><span data-stu-id="04e25-241">The `Enable-PSRemoting` cmdlet creates the default session configurations on your computer: Microsoft.PowerShell, Microsoft.PowerShell.Workflow, and Microsoft.PowerShell32 (64-bit operating systems only).</span></span> <span data-ttu-id="04e25-242">`Enable-PSRemoting` anger säkerhets beskrivningen för konfigurationen så att endast medlemmar i gruppen Administratörer på datorn kan använda dem.</span><span class="sxs-lookup"><span data-stu-id="04e25-242">`Enable-PSRemoting` sets the security descriptor for the configuration to allow only members of the Administrators group on your computer to use them.</span></span>

<span data-ttu-id="04e25-243">Du kan använda konfigurations-cmdletar för sessioner för att redigera standardkonfigurationerna för sessioner, skapa nya sessionsinställningar och ändra säkerhets beskrivare för alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="04e25-243">You can use the session configuration cmdlets to edit the default session configurations, to create new session configurations, and to change the security descriptors of all the session configurations.</span></span>

<span data-ttu-id="04e25-244">Från och med Windows PowerShell 3,0 `New-PSSessionConfigurationFile` kan du skapa anpassade sessionsnycklar med hjälp av en textfil.</span><span class="sxs-lookup"><span data-stu-id="04e25-244">Beginning in Windows PowerShell 3.0, the `New-PSSessionConfigurationFile` cmdlet lets you create custom session configurations by using a text file.</span></span> <span data-ttu-id="04e25-245">Filen innehåller alternativ för att ställa in språk läget och för att ange de cmdletar och moduler som är tillgängliga i sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-245">The file includes options for setting the language mode and for specifying the cmdlets and modules that are available in sessions that use the session configuration.</span></span>

<span data-ttu-id="04e25-246">När användarna använder `Invoke-Command` `New-PSSession` cmdletarna, eller, `Enter-PSSession` kan de använda **ConfigurationName** -parametern för att ange den sessionsinformation som används för sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-246">When users use the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets, they can use the **ConfigurationName** parameter to indicate the session configuration that is used for the session.</span></span> <span data-ttu-id="04e25-247">Dessutom kan de ändra standard konfigurationen som deras sessioner använder genom att ändra värdet för `$PSSessionConfigurationName` variabeln Preference i sessionen.</span><span class="sxs-lookup"><span data-stu-id="04e25-247">And, they can change the default configuration that their sessions use by changing the value of the `$PSSessionConfigurationName` preference variable in the session.</span></span>

<span data-ttu-id="04e25-248">Mer information om sessionsbaserade finns i hjälpen för cmdletarna för session konfiguration.</span><span class="sxs-lookup"><span data-stu-id="04e25-248">For more information about session configurations, see the Help for the session configuration cmdlets.</span></span> <span data-ttu-id="04e25-249">Om du vill hitta sessionens konfigurations-cmdletar skriver du:</span><span class="sxs-lookup"><span data-stu-id="04e25-249">To find the session configuration cmdlets, type:</span></span>

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a><span data-ttu-id="04e25-250">Vad är fläkt i och fläktiga konfigurationer?</span><span class="sxs-lookup"><span data-stu-id="04e25-250">What are fan in and fan out configurations?</span></span>

<span data-ttu-id="04e25-251">Det vanligaste scenariot för PowerShell-fjärrkommunikation som omfattar flera datorer är en-till-många-konfiguration, där en lokal dator (administratörens dator) kör PowerShell-kommandon på flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="04e25-251">The most common PowerShell remoting scenario involving multiple computers is the one-to-many configuration, in which one local computer (the administrator's computer) runs PowerShell commands on numerous remote computers.</span></span> <span data-ttu-id="04e25-252">Detta kallas för "fläkt ut"-scenariot.</span><span class="sxs-lookup"><span data-stu-id="04e25-252">This is known as the "fan-out" scenario.</span></span>

<span data-ttu-id="04e25-253">I vissa företag är konfigurationen emellertid många-till-en, där många klient datorer ansluter till en enda fjärrdator som kör PowerShell, till exempel en fil server eller en kiosk.</span><span class="sxs-lookup"><span data-stu-id="04e25-253">However, in some enterprises, the configuration is many-to-one, where many client computers connect to a single remote computer that is running PowerShell, such as a file server or a kiosk.</span></span> <span data-ttu-id="04e25-254">Detta kallas för "fläkt-in"-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="04e25-254">This is known as the "fan-in" configuration.</span></span>

<span data-ttu-id="04e25-255">PowerShell-fjärrkommunikation stöder både fläkt-och fläkt konfiguration.</span><span class="sxs-lookup"><span data-stu-id="04e25-255">PowerShell remoting supports both fan-out and fan-in configurations.</span></span>

<span data-ttu-id="04e25-256">För fläkt konfigurationen använder PowerShell protokollet webb tjänster för hantering (WS-Management) och den WinRM-tjänst som stöder Microsoft-implementeringen av WS-Management.</span><span class="sxs-lookup"><span data-stu-id="04e25-256">For the fan-out configuration, PowerShell uses the Web Services for Management (WS-Management) protocol and the WinRM service that supports the Microsoft implementation of WS-Management.</span></span> <span data-ttu-id="04e25-257">När en lokal dator ansluter till en fjärrdator upprättar WS-Management en anslutning och använder ett plugin-program för PowerShell för att starta PowerShell-värd processen (Wsmprovhost.exe) på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-257">When a local computer connects to a remote computer, WS-Management establishes a connection and uses a plug-in for PowerShell to start the PowerShell host process (Wsmprovhost.exe) on the remote computer.</span></span> <span data-ttu-id="04e25-258">Användaren kan ange en alternativ port, en alternativ konfiguration av sessionen och andra funktioner för att anpassa fjärr anslutningen.</span><span class="sxs-lookup"><span data-stu-id="04e25-258">The user can specify an alternate port, an alternate session configuration, and other features to customize the remote connection.</span></span>

<span data-ttu-id="04e25-259">För att stödja "fläkt-in"-konfigurationen använder PowerShell IIS (Internet Information Services) för att hantera WS-Management, läsa in PowerShell-plugin-programmet och starta PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04e25-259">To support the "fan-in" configuration, PowerShell uses internet Information Services (IIS) to host WS-Management, to load the PowerShell plug-in, and to start PowerShell.</span></span> <span data-ttu-id="04e25-260">I det här scenariot, i stället för att starta varje PowerShell-session i en separat process, körs alla PowerShell-sessioner i samma värd process.</span><span class="sxs-lookup"><span data-stu-id="04e25-260">In this scenario, instead of starting each PowerShell session in a separate process, all PowerShell sessions run in the same host process.</span></span>

<span data-ttu-id="04e25-261">IIS-värd och fläkt-in-fjärrhantering stöds inte i Windows XP eller Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="04e25-261">IIS hosting and fan-in remote management is not supported in Windows XP or in Windows Server 2003.</span></span>

<span data-ttu-id="04e25-262">I en fläkt konfiguration kan användaren ange en anslutnings-URI och en HTTP-slutpunkt, inklusive transport, dator namn, port och program namn.</span><span class="sxs-lookup"><span data-stu-id="04e25-262">In a fan-in configuration, the user can specify a connection URI and an HTTP endpoint, including the transport, computer name, port, and application name.</span></span>
<span data-ttu-id="04e25-263">IIS vidarebefordrar alla förfrågningar med ett angivet program namn till programmet.</span><span class="sxs-lookup"><span data-stu-id="04e25-263">IIS forwards all the requests with a specified application name to the application.</span></span> <span data-ttu-id="04e25-264">Standardvärdet är WS-Management, som kan vara värd för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04e25-264">The default is WS-Management, which can host PowerShell.</span></span>

<span data-ttu-id="04e25-265">Du kan också ange en autentiseringsmekanism och förhindra eller tillåta omdirigering från HTTP-och HTTPS-slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="04e25-265">You can also specify an authentication mechanism and prohibit or allow redirection from HTTP and HTTPS endpoints.</span></span>

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a><span data-ttu-id="04e25-266">Kan jag testa fjärr kommunikation på en enskild dator som inte är i en domän?</span><span class="sxs-lookup"><span data-stu-id="04e25-266">Can I test remoting on a single computer not in a domain?</span></span>

<span data-ttu-id="04e25-267">Ja.</span><span class="sxs-lookup"><span data-stu-id="04e25-267">Yes.</span></span> <span data-ttu-id="04e25-268">PowerShell-fjärrkommunikation är tillgängligt även när den lokala datorn inte finns i en domän.</span><span class="sxs-lookup"><span data-stu-id="04e25-268">PowerShell remoting is available even when the local computer is not in a domain.</span></span> <span data-ttu-id="04e25-269">Du kan använda funktionerna för fjärr anslutning för att ansluta till sessioner och för att skapa sessioner på samma dator.</span><span class="sxs-lookup"><span data-stu-id="04e25-269">You can use the remoting features to connect to sessions and to create sessions on the same computer.</span></span> <span data-ttu-id="04e25-270">Funktionerna fungerar på samma sätt som när du ansluter till en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="04e25-270">The features work the same as they do when you connect to a remote computer.</span></span>

<span data-ttu-id="04e25-271">Om du vill köra fjärrkommandon på en dator i en arbets grupp ändrar du följande Windows-inställningar på datorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-271">To run remote commands on a computer in a workgroup, change the following Windows settings on the computer.</span></span>

<span data-ttu-id="04e25-272">Varning! de här inställningarna påverkar alla användare i systemet och de kan göra systemet mer sårbart för angrepp.</span><span class="sxs-lookup"><span data-stu-id="04e25-272">Caution: These settings affect all users on the system and they can make the system more vulnerable to a malicious attack.</span></span> <span data-ttu-id="04e25-273">Var försiktig när du gör dessa ändringar.</span><span class="sxs-lookup"><span data-stu-id="04e25-273">Use caution when making these changes.</span></span>

- <span data-ttu-id="04e25-274">Windows Vista, Windows 7, Windows 8:</span><span class="sxs-lookup"><span data-stu-id="04e25-274">Windows Vista, Windows 7, Windows 8:</span></span>

  <span data-ttu-id="04e25-275">Skapa följande register post och ange värdet till 1: LocalAccountTokenFilterPolicy i ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span><span class="sxs-lookup"><span data-stu-id="04e25-275">Create the following registry entry, and then set its value to 1: LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span></span>

  <span data-ttu-id="04e25-276">Du kan använda följande PowerShell-kommando för att lägga till följande post:</span><span class="sxs-lookup"><span data-stu-id="04e25-276">You can use the following PowerShell command to add this entry:</span></span>

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- <span data-ttu-id="04e25-277">Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:</span><span class="sxs-lookup"><span data-stu-id="04e25-277">Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:</span></span>

  <span data-ttu-id="04e25-278">Inga ändringar krävs eftersom standardinställningen för principen "nätverks åtkomst: delning och säkerhets modell för lokala konton" är "klassisk".</span><span class="sxs-lookup"><span data-stu-id="04e25-278">No changes are needed because the default setting of the "Network Access: Sharing and security model for local accounts" policy is "Classic".</span></span> <span data-ttu-id="04e25-279">Kontrol lera inställningen om den har ändrats.</span><span class="sxs-lookup"><span data-stu-id="04e25-279">Verify the setting in case it has changed.</span></span>

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a><span data-ttu-id="04e25-280">Kan jag köra fjärrkommandon på en dator i en annan domän?</span><span class="sxs-lookup"><span data-stu-id="04e25-280">Can I run remote commands on a computer in another domain?</span></span>

<span data-ttu-id="04e25-281">Ja.</span><span class="sxs-lookup"><span data-stu-id="04e25-281">Yes.</span></span> <span data-ttu-id="04e25-282">Vanligt vis körs kommandona utan fel, men du kan behöva använda parametern **Credential** för `Invoke-Command` `New-PSSession` `Enter-PSSession` cmdletarna, eller för att ange autentiseringsuppgifter för en medlem i gruppen Administratörer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-282">Typically, the commands run without error, although you might need to use the **Credential** parameter of the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets to provide the credentials of a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="04e25-283">Detta krävs ibland även om den aktuella användaren är medlem i gruppen Administratörer på den lokala datorn och fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="04e25-283">This is sometimes required even when the current user is a member of the Administrators group on the local and remote computers.</span></span>

<span data-ttu-id="04e25-284">Men om fjärrdatorn inte finns i en domän som den lokala datorn litar på, kanske inte fjärrdatorn kan autentisera användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="04e25-284">However, if the remote computer is not in a domain that the local computer trusts, the remote computer might not be able to authenticate the user's credentials.</span></span>

<span data-ttu-id="04e25-285">Om du vill aktivera autentisering använder du följande kommando för att lägga till fjärrdatorn i listan över betrodda värdar för den lokala datorn i WinRM.</span><span class="sxs-lookup"><span data-stu-id="04e25-285">To enable authentication, use the following command to add the remote computer to the list of trusted hosts for the local computer in WinRM.</span></span> <span data-ttu-id="04e25-286">Skriv kommandot vid PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="04e25-286">Type the command at the PowerShell prompt.</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

<span data-ttu-id="04e25-287">Om du till exempel vill lägga till Server01-datorn i listan över betrodda värdar på den lokala datorn skriver du följande kommando i PowerShell-prompten:</span><span class="sxs-lookup"><span data-stu-id="04e25-287">For example, to add the Server01 computer to the list of trusted hosts on the local computer, type the following command at the PowerShell prompt:</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```


## <a name="see-also"></a><span data-ttu-id="04e25-288">Se även</span><span class="sxs-lookup"><span data-stu-id="04e25-288">See also</span></span>

[<span data-ttu-id="04e25-289">about_Remote</span><span class="sxs-lookup"><span data-stu-id="04e25-289">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="04e25-290">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="04e25-290">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="04e25-291">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="04e25-291">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="04e25-292">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="04e25-292">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)

[<span data-ttu-id="04e25-293">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="04e25-293">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="04e25-294">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="04e25-294">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="04e25-295">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="04e25-295">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
