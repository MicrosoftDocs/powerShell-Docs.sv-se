---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: f4fe65ec687ca39c1356dd5c9a590899c8b3789c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346011"
---
# <span data-ttu-id="e05b0-103">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="e05b0-103">Disable-PSRemoting</span></span>

## <span data-ttu-id="e05b0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e05b0-104">SYNOPSIS</span></span>
<span data-ttu-id="e05b0-105">Förhindrar att PowerShell-slutpunkter tar emot fjärr anslutningar.</span><span class="sxs-lookup"><span data-stu-id="e05b0-105">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="e05b0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e05b0-106">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e05b0-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e05b0-107">DESCRIPTION</span></span>

<span data-ttu-id="e05b0-108">`Disable-PSRemoting`Cmdleten blockerar fjärråtkomst till alla PowerShell version 6 och större konfigurationer för sessionens slut punkt på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-108">The `Disable-PSRemoting` cmdlet blocks remote access to all PowerShell version 6 and greater session endpoint configurations on the local computer.</span></span> <span data-ttu-id="e05b0-109">Konfigurationen för Windows PowerShell-slutpunkter påverkas inte.</span><span class="sxs-lookup"><span data-stu-id="e05b0-109">It does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="e05b0-110">Om du vill inaktivera slut punkts konfiguration för Windows PowerShell kör du kommandot inifrån `Disable-PSRemoting` en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e05b0-110">To disable Windows PowerShell session endpoint configurations, run `Disable-PSRemoting` command from within a Windows PowerShell session.</span></span>

<span data-ttu-id="e05b0-111">Använd cmdleten för att återaktivera fjärråtkomst till alla PowerShell version 6 och fler konfigurationer för sessionens slut punkt `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="e05b0-111">To re-enable remote access to all PowerShell version 6 and greater session endpoint configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="e05b0-112">Om du vill återaktivera fjärråtkomst till alla Windows PowerShell-sessionens slut punkts konfiguration, kör du i `Enable-PSRemoting` en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e05b0-112">To re-enable remote access to all Windows PowerShell session endpoint configurations, run `Enable-PSRemoting` from within a Windows PowerShell session.</span></span>

> [!NOTE]
> <span data-ttu-id="e05b0-113">Om du vill inaktivera all PowerShell-fjärråtkomst till en lokal Windows-dator måste du köra det här kommandot både från en i PowerShell version 6 eller en senare session och inifrån en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e05b0-113">If you want to disable all PowerShell remote access to a local Windows machine, you must run this command both from a within PowerShell version 6 or greater session and from within a Windows PowerShell session.</span></span> <span data-ttu-id="e05b0-114">Windows PowerShell installeras som standard på alla Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="e05b0-114">Windows PowerShell is installed on all Windows machines by default.</span></span>

<span data-ttu-id="e05b0-115">Om du vill inaktivera och återaktivera fjärråtkomst till en speciell sessions slut punkts konfiguration använder du `Enable-PSSessionConfiguration` `Disable-PSSessionConfiguration` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="e05b0-115">To disable and re-enable remote access to specific session endpoint configurations, use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="e05b0-116">Om du vill ange specifika åtkomst konfigurationer för enskilda slut punkter använder du `Set-PSSessionConfiguration` cmdleten tillsammans med parametern **AccessMode** .</span><span class="sxs-lookup"><span data-stu-id="e05b0-116">To set specific access configurations of individual endpoints, use the `Set-PSSessionConfiguration` cmdlet along with the **AccessMode** parameter.</span></span> <span data-ttu-id="e05b0-117">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="e05b0-117">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e05b0-118">Trots att `Disable-PSRemoting` du har kört kan du fortfarande göra loopback-anslutningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-118">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="e05b0-119">En loopback-anslutning är en PowerShell-fjärrsession som kommer från och ansluter till samma lokala dator.</span><span class="sxs-lookup"><span data-stu-id="e05b0-119">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="e05b0-120">Fjärrsessioner från externa källor förblir blockerade.</span><span class="sxs-lookup"><span data-stu-id="e05b0-120">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="e05b0-121">För loopback-anslutningar måste du använda implicita autentiseringsuppgifter tillsammans med parametern **EnableNetworkAccess** .</span><span class="sxs-lookup"><span data-stu-id="e05b0-121">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="e05b0-122">Mer information om loopback-anslutningar finns i [New-PSSession](New-PSSession.md).</span><span class="sxs-lookup"><span data-stu-id="e05b0-122">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="e05b0-123">Den här cmdleten är endast tillgänglig på Windows-plattformen.</span><span class="sxs-lookup"><span data-stu-id="e05b0-123">This cmdlet is only available on the Windows platform.</span></span> <span data-ttu-id="e05b0-124">Den är inte tillgänglig på Linux-eller macOS-versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e05b0-124">It is not available on Linux or macOS versions of PowerShell.</span></span> <span data-ttu-id="e05b0-125">Starta PowerShell med alternativet **Kör som administratör** för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e05b0-125">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="e05b0-126">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e05b0-126">EXAMPLES</span></span>

### <span data-ttu-id="e05b0-127">Exempel 1: förhindra fjärråtkomst till alla PowerShell-sessionsbaserade konfigurationer</span><span class="sxs-lookup"><span data-stu-id="e05b0-127">Example 1: Prevent remote access to all PowerShell session configurations</span></span>

<span data-ttu-id="e05b0-128">Det här exemplet förhindrar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-128">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="e05b0-129">Exempel 2: förhindra fjärråtkomst till alla PowerShell-sessionsbaserade utan bekräftelse meddelande</span><span class="sxs-lookup"><span data-stu-id="e05b0-129">Example 2: Prevent remote access to all PowerShell session configurations without confirmation prompt</span></span>

<span data-ttu-id="e05b0-130">Det här exemplet förhindrar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn utan att du behöver ange något.</span><span class="sxs-lookup"><span data-stu-id="e05b0-130">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="e05b0-131">Exempel 3: effekterna av att köra denna cmdlet</span><span class="sxs-lookup"><span data-stu-id="e05b0-131">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="e05b0-132">I det här exemplet visas effekterna av att använda `Disable-PSRemoting` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e05b0-132">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="e05b0-133">Starta PowerShell med alternativet **Kör som administratör** för att köra den här kommando sekvensen.</span><span class="sxs-lookup"><span data-stu-id="e05b0-133">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="e05b0-134">När du har inaktiverat sessionerna `New-PSSession` försöker cmdleten skapa en fjärrsession till den lokala datorn (kallas även "loopback").</span><span class="sxs-lookup"><span data-stu-id="e05b0-134">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="e05b0-135">Eftersom fjärråtkomst är inaktive rad på den lokala datorn Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="e05b0-135">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### <span data-ttu-id="e05b0-136">Exempel 4: effekterna av att köra denna cmdlet och Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="e05b0-136">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="e05b0-137">I det här exemplet visas effekterna av sessionens konfigurationer av med hjälp av `Disable-PSRemoting` `Enable-PSRemoting` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="e05b0-137">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="e05b0-138">`Disable-PSRemoting` används för att inaktivera fjärråtkomst till alla PowerShell-sessioner för slut punkts konfiguration.</span><span class="sxs-lookup"><span data-stu-id="e05b0-138">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="e05b0-139">Parametern **Force** förhindrar alla användar meddelanden.</span><span class="sxs-lookup"><span data-stu-id="e05b0-139">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="e05b0-140">`Get-PSSessionConfiguration` `Format-Table` Cmdletarna och visar sessionens konfigurationer på datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-140">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="e05b0-141">Utdata visar att alla fjärran vändare med en nätverks-token nekas åtkomst till slut punkts konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="e05b0-141">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="e05b0-142">Gruppen Administratörer på den lokala datorn får åtkomst till slut punkts konfigurationerna så länge de ansluter lokalt (kallas även loopback) och använder implicita autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="e05b0-142">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

<span data-ttu-id="e05b0-143">`Enable-PSRemoting`Cmdleten återaktiverar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-143">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="e05b0-144">**Force** -parametern utelämnar alla användar meddelanden och startar om WinRM-tjänsten utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="e05b0-144">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="e05b0-145">De nya utdata visar att **AccessDenied** säkerhets beskrivningar har tagits bort från alla sessionsinställningar.</span><span class="sxs-lookup"><span data-stu-id="e05b0-145">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="e05b0-146">Exempel 5: loopback-anslutningar med inaktiverade sessioner med slut punkts konfiguration</span><span class="sxs-lookup"><span data-stu-id="e05b0-146">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="e05b0-147">Det här exemplet visar hur slut punkts konfigurationen är inaktive rad och hur du gör en lyckad loopback-anslutning till en inaktive rad slut punkt.</span><span class="sxs-lookup"><span data-stu-id="e05b0-147">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="e05b0-148">`Disable-PSRemoting` inaktiverar alla slut punkts konfigurationer för PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="e05b0-148">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="e05b0-149">Den första användningen av `New-PSSession` försök att skapa en fjärrsession till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-149">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="e05b0-150">Parametern **ConfigurationName** används för att ange en inaktive rad PowerShell-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="e05b0-150">The **ConfigurationName** parameter is used to specify a disabled PowerShell endpoint.</span></span> <span data-ttu-id="e05b0-151">Autentiseringsuppgifter skickas explicit till kommandot via parametern för **autentiseringsuppgifter** .</span><span class="sxs-lookup"><span data-stu-id="e05b0-151">Credentials are explicitly passed to the command through the **Credential** parameter.</span></span> <span data-ttu-id="e05b0-152">Den här typen av anslutning går igenom nätverks stacken och är inte en loopback.</span><span class="sxs-lookup"><span data-stu-id="e05b0-152">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="e05b0-153">Det innebär att anslutnings försöket till den inaktiverade slut punkten Miss lyckas med fel meddelandet **åtkomst nekas** .</span><span class="sxs-lookup"><span data-stu-id="e05b0-153">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="e05b0-154">Den andra användningen av `New-PSSession` försöker också att skapa en fjärrsession till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-154">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="e05b0-155">I det här fallet lyckas det eftersom det är en loopback-anslutning som kringgår nätverks stacken.</span><span class="sxs-lookup"><span data-stu-id="e05b0-155">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="e05b0-156">En loopback-anslutning skapas när följande villkor uppfylls:</span><span class="sxs-lookup"><span data-stu-id="e05b0-156">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="e05b0-157">Dator namnet som ska anslutas till är localhost.</span><span class="sxs-lookup"><span data-stu-id="e05b0-157">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="e05b0-158">Inga autentiseringsuppgifter har skickats.</span><span class="sxs-lookup"><span data-stu-id="e05b0-158">No credentials are passed in.</span></span> <span data-ttu-id="e05b0-159">Den aktuella inloggade användaren (implicita autentiseringsuppgifter) används för anslutningen.</span><span class="sxs-lookup"><span data-stu-id="e05b0-159">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="e05b0-160">Växel parametern **EnableNetworkAccess** används.</span><span class="sxs-lookup"><span data-stu-id="e05b0-160">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="e05b0-161">Mer information om loopback-anslutningar finns i [New-PSSession](New-PSSession.md) Document.</span><span class="sxs-lookup"><span data-stu-id="e05b0-161">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="e05b0-162">Exempel 6: inaktivera alla konfigurationer för PowerShell-fjärrkörning av slut punkter</span><span class="sxs-lookup"><span data-stu-id="e05b0-162">Example 6: Disabling all PowerShell remoting endpoint configurations</span></span>

<span data-ttu-id="e05b0-163">Det här exemplet visar hur körning av `Disable-PSRemoting` kommandot inte påverkar konfigurationen av Windows PowerShell-slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="e05b0-163">This example demonstrates how running the `Disable-PSRemoting` command does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="e05b0-164">`Get-PSSessionConfiguration` Kör i Windows PowerShell visar alla slut punkts konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="e05b0-164">`Get-PSSessionConfiguration` run within Windows PowerShell shows all endpoint configurations.</span></span> <span data-ttu-id="e05b0-165">Vi ser att konfigurationerna för Windows PowerShell-slutpunkten inte är inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="e05b0-165">We see that the Windows PowerShell endpoint configurations are not disabled.</span></span>

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

<span data-ttu-id="e05b0-166">Om du vill inaktivera de här slut punkts konfigurationerna `Disable-PSRemoting` måste kommandot köras inifrån en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e05b0-166">To disable these endpoint configurations, the `Disable-PSRemoting` command must be run from within a Windows PowerShell session.</span></span> <span data-ttu-id="e05b0-167">Nu kan du `Get-PSSessionConfiguration` köra från Windows PowerShell och se att alla Endpoint-konfigurationer är inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="e05b0-167">Now, `Get-PSSessionConfiguration` run from within Windows PowerShell shows that all endpoint configurations are disabled.</span></span>

### <span data-ttu-id="e05b0-168">Exempel 7: förhindra fjärråtkomst till sessionsinställningar som har anpassade säkerhets beskrivningar</span><span class="sxs-lookup"><span data-stu-id="e05b0-168">Example 7: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="e05b0-169">Det här exemplet visar att- `Disable-PSRemoting` cmdleten inaktiverar fjärråtkomst till alla sessionsinställningar som innehåller konfigurationer med anpassade säkerhets beskrivningar.</span><span class="sxs-lookup"><span data-stu-id="e05b0-169">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="e05b0-170">`Register-PSSessionConfiguration`skapar en **Test** testsessions-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="e05b0-170">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="e05b0-171">Parametern **sökväg** anger en konfigurations fil för sessionen som anpassar sessionen.</span><span class="sxs-lookup"><span data-stu-id="e05b0-171">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="e05b0-172">Parametern **ShowSecurityDescriptorUI** visar en dialog ruta som anger behörigheter för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="e05b0-172">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="e05b0-173">I dialog rutan behörigheter skapar vi anpassade fullständiga åtkomst behörigheter för den angivna användaren.</span><span class="sxs-lookup"><span data-stu-id="e05b0-173">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="e05b0-174">`Get-PSSessionConfiguration` `Format-Table` Cmdletarna och visar sessionens konfigurationer och deras egenskaper.</span><span class="sxs-lookup"><span data-stu-id="e05b0-174">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="e05b0-175">Utdata visar att **testsessionens** konfiguration tillåter interaktiv åtkomst och särskilda behörigheter för den angivna användaren.</span><span class="sxs-lookup"><span data-stu-id="e05b0-175">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="e05b0-176">`Disable-PSRemoting` inaktiverar fjärråtkomst till alla konfigurationer för sessioner.</span><span class="sxs-lookup"><span data-stu-id="e05b0-176">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

<span data-ttu-id="e05b0-177">Nu `Get-PSSessionConfiguration` visar-och `Format-Table` -cmdletarna att en **AccessDenied** säkerhets beskrivning för alla nätverks användare läggs till i alla konfigurationer för sessioner, **Test** inklusive konfigurationen för testsession.</span><span class="sxs-lookup"><span data-stu-id="e05b0-177">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="e05b0-178">Även om de andra säkerhets beskrivarna inte ändras har säkerhets beskrivningen "network_deny_all" företräde.</span><span class="sxs-lookup"><span data-stu-id="e05b0-178">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="e05b0-179">Detta illustreras med det försök att använda `New-PSSession` för att ansluta till **Test** konfigurationen av Testsessionen.</span><span class="sxs-lookup"><span data-stu-id="e05b0-179">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="e05b0-180">Exempel 8: återaktivera fjärråtkomst till valda sessionsbaserade</span><span class="sxs-lookup"><span data-stu-id="e05b0-180">Example 8: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="e05b0-181">Det här exemplet visar hur du återaktiverar fjärråtkomst enbart till valda sessionsinställningar.</span><span class="sxs-lookup"><span data-stu-id="e05b0-181">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="e05b0-182">När du har inaktiverat alla sessionsinställningar, återaktivera vi en speciell session.</span><span class="sxs-lookup"><span data-stu-id="e05b0-182">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="e05b0-183">`Set-PSSessionConfiguration`Cmdleten används för att ändra konfigurationen för **PowerShell. 6** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="e05b0-183">The `Set-PSSessionConfiguration` cmdlet is used to change the **PowerShell.6** session configuration.</span></span> <span data-ttu-id="e05b0-184">Parametern **AccessMode** med värdet **fjärran sluten** för fjärråtkomst återaktiverar fjärråtkomst till konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="e05b0-184">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

## <span data-ttu-id="e05b0-185">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e05b0-185">PARAMETERS</span></span>

### <span data-ttu-id="e05b0-186">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e05b0-186">-Confirm</span></span>

<span data-ttu-id="e05b0-187">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e05b0-187">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e05b0-188">-Force</span><span class="sxs-lookup"><span data-stu-id="e05b0-188">-Force</span></span>

<span data-ttu-id="e05b0-189">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="e05b0-189">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e05b0-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e05b0-190">-WhatIf</span></span>

<span data-ttu-id="e05b0-191">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e05b0-191">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e05b0-192">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e05b0-192">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e05b0-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e05b0-193">CommonParameters</span></span>

<span data-ttu-id="e05b0-194">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e05b0-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e05b0-195">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e05b0-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e05b0-196">INDATA</span><span class="sxs-lookup"><span data-stu-id="e05b0-196">INPUTS</span></span>

### <span data-ttu-id="e05b0-197">Inget</span><span class="sxs-lookup"><span data-stu-id="e05b0-197">None</span></span>

<span data-ttu-id="e05b0-198">Det går inte att skicka några objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e05b0-198">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="e05b0-199">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e05b0-199">OUTPUTS</span></span>

### <span data-ttu-id="e05b0-200">Inget</span><span class="sxs-lookup"><span data-stu-id="e05b0-200">None</span></span>

<span data-ttu-id="e05b0-201">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e05b0-201">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e05b0-202">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e05b0-202">NOTES</span></span>

<span data-ttu-id="e05b0-203">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="e05b0-203">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="e05b0-204">Om du inaktiverar-sessionsinställningar återställs inte alla ändringar som har gjorts av `Enable-PSRemoting` `Enable-PSSessionConfiguration` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="e05b0-204">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="e05b0-205">Du kan behöva ångra följande ändringar manuellt.</span><span class="sxs-lookup"><span data-stu-id="e05b0-205">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="e05b0-206">Stoppa och inaktivera WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e05b0-206">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="e05b0-207">Ta bort den lyssnare som accepterar begär Anden på alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="e05b0-207">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="e05b0-208">Inaktivera brand Väggs undantag för WS-Management kommunikation.</span><span class="sxs-lookup"><span data-stu-id="e05b0-208">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="e05b0-209">Återställ värdet för LocalAccountTokenFilterPolicy till 0, vilket begränsar fjärråtkomst till medlemmar i gruppen Administratörer på datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-209">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

- <span data-ttu-id="e05b0-210">En sessions slut punkts konfiguration är en grupp inställningar som definierar miljön för en session.</span><span class="sxs-lookup"><span data-stu-id="e05b0-210">A session endpoint configuration is a group of settings that define the environment for a session.</span></span>
  <span data-ttu-id="e05b0-211">Varje session som ansluter till datorn måste använda en av sessionens slut punkts konfigurationer som är registrerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-211">Every session that connects to the computer must use one of the session endpoint configurations that are registered on the computer.</span></span> <span data-ttu-id="e05b0-212">Genom att neka fjärråtkomst till alla konfigurationer för sessionens slut punkt hindrar du effektivt att fjärranslutna användare upprättar sessioner som ansluter till datorn.</span><span class="sxs-lookup"><span data-stu-id="e05b0-212">By denying remote access to all session endpoint configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

## <span data-ttu-id="e05b0-213">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e05b0-213">RELATED LINKS</span></span>

[<span data-ttu-id="e05b0-214">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e05b0-214">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="e05b0-215">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="e05b0-215">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="e05b0-216">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e05b0-216">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="e05b0-217">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e05b0-217">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="e05b0-218">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e05b0-218">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="e05b0-219">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e05b0-219">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="e05b0-220">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e05b0-220">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="e05b0-221">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="e05b0-221">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
