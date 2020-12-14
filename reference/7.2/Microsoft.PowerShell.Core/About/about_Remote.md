---
description: Beskriver hur du kör fjärrkommandon i PowerShell.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: b47efbaaebdd75be5f15be449e194113a0d6ebd7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708438"
---
# <a name="about-remote"></a><span data-ttu-id="148d1-103">Om fjärran sluten</span><span class="sxs-lookup"><span data-stu-id="148d1-103">About Remote</span></span>

## <a name="short-description"></a><span data-ttu-id="148d1-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="148d1-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="148d1-105">Beskriver hur du kör fjärrkommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="148d1-105">Describes how to run remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="148d1-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="148d1-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="148d1-107">Du kan köra fjärrkommandon på en enskild dator eller på flera datorer genom att använda en tillfällig eller permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="148d1-107">You can run remote commands on a single computer or on multiple computers by using a temporary or persistent connection.</span></span> <span data-ttu-id="148d1-108">Du kan också starta en interaktiv session med en enda fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="148d1-108">You can also start an interactive session with a single remote computer.</span></span>

<span data-ttu-id="148d1-109">Det här avsnittet innehåller en serie exempel som visar hur du kör olika typer av fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="148d1-109">This topic provides a series of examples to show you how to run different types of remote command.</span></span> <span data-ttu-id="148d1-110">När du har provat de här grundläggande kommandona läser du de hjälp avsnitt som beskriver varje cmdlet som används i de här kommandona.</span><span class="sxs-lookup"><span data-stu-id="148d1-110">After you try these basic commands, read the Help topics that describe each cmdlet that is used in these commands.</span></span> <span data-ttu-id="148d1-111">Avsnitten innehåller information och förklarar hur du kan ändra kommandona så att de passar dina behov.</span><span class="sxs-lookup"><span data-stu-id="148d1-111">The topics provide the details and explain how you can modify the commands to meet your needs.</span></span>

<span data-ttu-id="148d1-112">Obs: om du vill använda PowerShell-fjärrkommunikation måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="148d1-112">Note: To use PowerShell remoting, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="148d1-113">Mer information finns i [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="148d1-113">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="how-to-start-an-interactive-session-enter-pssession"></a><span data-ttu-id="148d1-114">STARTA EN INTERAKTIV SESSION (RETUR-PSSESSION)</span><span class="sxs-lookup"><span data-stu-id="148d1-114">HOW TO START AN INTERACTIVE SESSION (ENTER-PSSESSION)</span></span>

<span data-ttu-id="148d1-115">Det enklaste sättet att köra fjärrkommandon är att starta en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="148d1-115">The easiest way to run remote commands is to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="148d1-116">När sessionen startar, de kommandon som du skriver körs på fjärrdatorn, precis som om du skrev dem direkt på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="148d1-116">When the session starts, the commands that you type run on the remote computer, just as though you typed them directly on the remote computer.</span></span> <span data-ttu-id="148d1-117">Du kan bara ansluta till en dator i varje interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="148d1-117">You can connect to only one computer in each interactive session.</span></span>

<span data-ttu-id="148d1-118">Använd Enter-PSSession-cmdleten för att starta en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="148d1-118">To start an interactive session, use the Enter-PSSession cmdlet.</span></span> <span data-ttu-id="148d1-119">Följande kommando startar en interaktiv session med Server01-datorn:</span><span class="sxs-lookup"><span data-stu-id="148d1-119">The following command starts an interactive session with the Server01 computer:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="148d1-120">Kommando tolken ändras för att indikera att du är ansluten till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="148d1-120">The command prompt changes to indicate that you are connected to the Server01 computer.</span></span>

```
Server01\PS>
```

<span data-ttu-id="148d1-121">Nu kan du skriva kommandon på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="148d1-121">Now, you can type commands on the Server01 computer.</span></span>

<span data-ttu-id="148d1-122">Om du vill avsluta den interaktiva sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="148d1-122">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="148d1-123">Mer information finns i Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="148d1-123">For more information, see Enter-PSSession.</span></span>

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a><span data-ttu-id="148d1-124">SÅ HÄR ANVÄNDER DU CMDLETAR SOM HAR EN COMPUTERNAME-PARAMETER FÖR ATT HÄMTA FJÄRRDATA</span><span class="sxs-lookup"><span data-stu-id="148d1-124">HOW TO USE CMDLETS THAT HAVE A COMPUTERNAME PARAMETER TO GET REMOTE DATA</span></span>

<span data-ttu-id="148d1-125">Flera cmdlets har en ComputerName-parameter som låter dig hämta objekt från fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="148d1-125">Several cmdlets have a ComputerName parameter that lets you get objects from remote computers.</span></span>

<span data-ttu-id="148d1-126">Eftersom dessa cmdlets inte använder WS-Management-baserade PowerShell-fjärrkommunikationer kan du använda parametern ComputerName för dessa cmdlet: ar på alla datorer som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="148d1-126">Because these cmdlets do not use WS-Management-based PowerShell remoting, you can use the ComputerName parameter of these cmdlets on any computer that is running PowerShell.</span></span> <span data-ttu-id="148d1-127">Datorerna behöver inte konfigureras för PowerShell-fjärrkommunikation och datorerna behöver inte uppfylla system kraven för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="148d1-127">The computers do not have to be configured for PowerShell remoting, and the computers do not have to meet the system requirements for remoting.</span></span>

<span data-ttu-id="148d1-128">Följande cmdletar har en ComputerName-parameter:</span><span class="sxs-lookup"><span data-stu-id="148d1-128">The following cmdlets have a ComputerName parameter:</span></span>

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

<span data-ttu-id="148d1-129">Följande kommando hämtar till exempel tjänsterna på den fjärranslutna Server01-datorn:</span><span class="sxs-lookup"><span data-stu-id="148d1-129">For example, the following command gets the services on the Server01 remote computer:</span></span>

```powershell
Get-Service -ComputerName Server01
```

<span data-ttu-id="148d1-130">Normalt har cmdletar som stöder fjärr kommunikation utan särskild konfiguration en **computername** -parameter och har inte någon **session** -parameter.</span><span class="sxs-lookup"><span data-stu-id="148d1-130">Typically, cmdlets that support remoting without special configuration have a **ComputerName** parameter and do not have a **Session** parameter.</span></span> <span data-ttu-id="148d1-131">Om du vill hitta dessa cmdletar i din session skriver du:</span><span class="sxs-lookup"><span data-stu-id="148d1-131">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a><span data-ttu-id="148d1-132">SÅ HÄR KÖR DU ETT FJÄRRKOMMANDO</span><span class="sxs-lookup"><span data-stu-id="148d1-132">HOW TO RUN A REMOTE COMMAND</span></span>

<span data-ttu-id="148d1-133">Använd Invoke-Command-cmdleten om du vill köra andra kommandon på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="148d1-133">To run other commands on remote computers, use the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="148d1-134">Om du vill köra ett enda kommando eller några orelaterade kommandon använder du parametern ComputerName i Invoke-Command för att ange fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="148d1-134">To run a single command or a few unrelated commands, use the ComputerName parameter of Invoke-Command to specify the remote computers.</span></span> <span data-ttu-id="148d1-135">Använd parametern script block för att ange kommandot.</span><span class="sxs-lookup"><span data-stu-id="148d1-135">Use the ScriptBlock parameter to specify the command.</span></span>

<span data-ttu-id="148d1-136">Följande kommando kör till exempel ett Get-Culture-kommando på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="148d1-136">For example, the following command runs a Get-Culture command on the Server01 computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="148d1-137">Parametern ComputerName är utformad för situationer där du kör ett enda kommando eller flera orelaterade kommandon på en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="148d1-137">The ComputerName parameter is designed for situation in which you run a single command or several unrelated commands on one or many computers.</span></span> <span data-ttu-id="148d1-138">Använd parametern session för att upprätta en permanent anslutning till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="148d1-138">To establish a persistent connection to a remote computer, use the Session parameter.</span></span>

## <a name="how-to-create-a-persistent-connection-pssession"></a><span data-ttu-id="148d1-139">SÅ HÄR SKAPAR DU EN PERMANENT ANSLUTNING (PSSESSION)</span><span class="sxs-lookup"><span data-stu-id="148d1-139">HOW TO CREATE A PERSISTENT CONNECTION (PSSESSION)</span></span>

<span data-ttu-id="148d1-140">När du använder parametern ComputerName i Invoke-Command-cmdlet: en upprättar Windows PowerShell en anslutning enbart för kommandot.</span><span class="sxs-lookup"><span data-stu-id="148d1-140">When you use the ComputerName parameter of the Invoke-Command cmdlet, Windows PowerShell establishes a connection just for the command.</span></span> <span data-ttu-id="148d1-141">Sedan stängs anslutningen när kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="148d1-141">Then, it closes the connection when the command is complete.</span></span> <span data-ttu-id="148d1-142">Variabler eller funktioner som definieras i kommandot går förlorade.</span><span class="sxs-lookup"><span data-stu-id="148d1-142">Any variables or functions that are defined in the command are lost.</span></span>

<span data-ttu-id="148d1-143">Använd New-PSSession-cmdleten om du vill skapa en permanent anslutning till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="148d1-143">To create a persistent connection to a remote computer, use the New-PSSession cmdlet.</span></span> <span data-ttu-id="148d1-144">Följande kommando skapar till exempel PSSessions på Server01-och Server02-datorerna och sparar PSSessions i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="148d1-144">For example, the following command creates PSSessions on the Server01 and Server02 computers and then saves the PSSessions in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="148d1-145">KÖRA KOMMANDON I EN PSSESSION</span><span class="sxs-lookup"><span data-stu-id="148d1-145">HOW TO RUN COMMANDS IN A PSSESSION</span></span>

<span data-ttu-id="148d1-146">Med en PSSession kan du köra en serie fjärrkommandon som delar data, t. ex. funktioner, alias och värden för variabler.</span><span class="sxs-lookup"><span data-stu-id="148d1-146">With a PSSession, you can run a series of remote commands that share data, like functions, aliases, and the values of variables.</span></span> <span data-ttu-id="148d1-147">Om du vill köra kommandon i en PSSession använder du parametern session i Invoke-Command-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="148d1-147">To run commands in a PSSession, use the Session parameter of the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="148d1-148">Följande kommando använder exempelvis cmdleten Invoke-Command för att köra ett Get-Process kommando i PSSessions på Server01-och Server02-datorerna.</span><span class="sxs-lookup"><span data-stu-id="148d1-148">For example, the following command uses the Invoke-Command cmdlet to run a Get-Process command in the PSSessions on the Server01 and Server02 computers.</span></span>
<span data-ttu-id="148d1-149">Kommandot sparar processerna i en $p-variabel i varje PSSession.</span><span class="sxs-lookup"><span data-stu-id="148d1-149">The command saves the processes in a $p variable in each PSSession.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

<span data-ttu-id="148d1-150">Eftersom PSSession använder en permanent anslutning kan du köra ett annat kommando i samma PSSession som använder variabeln $p.</span><span class="sxs-lookup"><span data-stu-id="148d1-150">Because the PSSession uses a persistent connection, you can run another command in the same PSSession that uses the $p variable.</span></span> <span data-ttu-id="148d1-151">Följande kommando räknar antalet processer som har sparats i $p.</span><span class="sxs-lookup"><span data-stu-id="148d1-151">The following command counts the number of processes saved in $p.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a><span data-ttu-id="148d1-152">SÅ HÄR KÖR DU ETT FJÄRRKOMMANDO PÅ FLERA DATORER</span><span class="sxs-lookup"><span data-stu-id="148d1-152">HOW TO RUN A REMOTE COMMAND ON MULTIPLE COMPUTERS</span></span>

<span data-ttu-id="148d1-153">Om du vill köra ett fjärrkommando på flera datorer skriver du alla dator namn i värdet för parametern ComputerName för Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="148d1-153">To run a remote command on multiple computers, type all of the computer names in the value of the ComputerName parameter of Invoke-Command.</span></span> <span data-ttu-id="148d1-154">Avgränsa namnen med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="148d1-154">Separate the names with commas.</span></span>

<span data-ttu-id="148d1-155">Följande kommando kör till exempel ett Get-Culture-kommando på tre datorer:</span><span class="sxs-lookup"><span data-stu-id="148d1-155">For example, the following command runs a Get-Culture command on three computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="148d1-156">Du kan också köra ett kommando i flera PSSessions.</span><span class="sxs-lookup"><span data-stu-id="148d1-156">You can also run a command in multiple PSSessions.</span></span> <span data-ttu-id="148d1-157">Följande kommandon skapar PSSessions på Server01-, Server02-och Server03-datorerna och kör sedan ett Get-Culture-kommando i varje PSSessions.</span><span class="sxs-lookup"><span data-stu-id="148d1-157">The following commands create PSSessions on the Server01, Server02, and Server03 computers and then run a Get-Culture command in each of the PSSessions.</span></span>

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="148d1-158">Om du vill ta med listan med lokala datorer, skriver du namnet på den lokala datorn, anger en punkt (.) eller skriver "localhost".</span><span class="sxs-lookup"><span data-stu-id="148d1-158">To include the local computer list of computers, type the name of the local computer, type a dot (.), or type  "localhost".</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a><span data-ttu-id="148d1-159">SÅ HÄR KÖR DU ETT SKRIPT PÅ FJÄRRDATORER</span><span class="sxs-lookup"><span data-stu-id="148d1-159">HOW TO RUN A SCRIPT ON REMOTE COMPUTERS</span></span>

<span data-ttu-id="148d1-160">Om du vill köra ett lokalt skript på fjärrdatorer använder du parametern sökväg för Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="148d1-160">To run a local script on remote computers, use the FilePath parameter of Invoke-Command.</span></span>

<span data-ttu-id="148d1-161">Följande kommando kör till exempel Sample.ps1-skriptet på datorerna S1 och S2:</span><span class="sxs-lookup"><span data-stu-id="148d1-161">For example, the following command runs the Sample.ps1 script on the S1 and S2 computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

<span data-ttu-id="148d1-162">Resultatet av skriptet returneras till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="148d1-162">The results of the script are returned to the local computer.</span></span> <span data-ttu-id="148d1-163">Du behöver inte kopiera några filer.</span><span class="sxs-lookup"><span data-stu-id="148d1-163">You do not need to copy any files.</span></span>

## <a name="how-to-stop-a-remote-command"></a><span data-ttu-id="148d1-164">SÅ HÄR STOPPAR DU ETT FJÄRRKOMMANDO</span><span class="sxs-lookup"><span data-stu-id="148d1-164">HOW TO STOP A REMOTE COMMAND</span></span>

<span data-ttu-id="148d1-165">Tryck på CTRL + C om du vill avbryta ett kommando.</span><span class="sxs-lookup"><span data-stu-id="148d1-165">To interrupt a command, press CTRL+C.</span></span> <span data-ttu-id="148d1-166">Avbrottsbegäran skickas till fjärrdatorn där den avslutar fjärrkommandot.</span><span class="sxs-lookup"><span data-stu-id="148d1-166">The interrupt request is passed to the remote computer where it terminates the remote command.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="148d1-167">MER INFORMATION</span><span class="sxs-lookup"><span data-stu-id="148d1-167">FOR MORE INFORMATION</span></span>

- <span data-ttu-id="148d1-168">Information om system kraven för fjärr kommunikation finns i [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="148d1-168">For information about the system requirements for remoting, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

- <span data-ttu-id="148d1-169">Information om hur du formaterar fjärrutdata finns i [about_Remote_Output](about_Remote_Output.md).</span><span class="sxs-lookup"><span data-stu-id="148d1-169">For help in formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

- <span data-ttu-id="148d1-170">Information om hur fjärr kommunikation fungerar, hur du hanterar fjärrdata, särskilda konfigurationer, säkerhets problem och andra vanliga frågor finns [about_Remote_FAQ](about_Remote_FAQ.md).</span><span class="sxs-lookup"><span data-stu-id="148d1-170">For information about how remoting works, how to manage remote data, special configurations, security issues, and other frequently asked questions, see [about_Remote_FAQ](about_Remote_FAQ.md).</span></span>

- <span data-ttu-id="148d1-171">Information om hur du löser fjärr kommunikations fel finns i about_Remote_Troubleshooting.</span><span class="sxs-lookup"><span data-stu-id="148d1-171">For help in resolving remoting errors, see about_Remote_Troubleshooting.</span></span>

- <span data-ttu-id="148d1-172">Information om PSSessions och beständiga anslutningar finns [about_PSSessions](about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="148d1-172">For information about PSSessions and persistent connections, see [about_PSSessions](about_PSSessions.md).</span></span>

- <span data-ttu-id="148d1-173">Information om PowerShell-bakgrunds jobb finns i [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="148d1-173">For information about PowerShell background jobs, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="148d1-174">RESERVERADE</span><span class="sxs-lookup"><span data-stu-id="148d1-174">KEYWORDS</span></span>

<span data-ttu-id="148d1-175">about_Remoting</span><span class="sxs-lookup"><span data-stu-id="148d1-175">about_Remoting</span></span>

## <a name="see-also"></a><span data-ttu-id="148d1-176">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="148d1-176">SEE ALSO</span></span>

[<span data-ttu-id="148d1-177">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="148d1-177">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="148d1-178">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="148d1-178">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="148d1-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="148d1-179">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="148d1-180">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="148d1-180">about_Remote_FAQ</span></span>](about_Remote_FAQ.md)

[<span data-ttu-id="148d1-181">about_Remote_TroubleShooting</span><span class="sxs-lookup"><span data-stu-id="148d1-181">about_Remote_TroubleShooting</span></span>](about_Remote_TroubleShooting.md)

[<span data-ttu-id="148d1-182">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="148d1-182">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="148d1-183">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="148d1-183">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="148d1-184">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="148d1-184">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="148d1-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="148d1-185">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

