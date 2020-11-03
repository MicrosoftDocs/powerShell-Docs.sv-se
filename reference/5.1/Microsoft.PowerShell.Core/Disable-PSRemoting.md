---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3a281786f99b2a46d0aeb9785480f02b35b2b433
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263667"
---
# <span data-ttu-id="9aca9-103">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="9aca9-103">Disable-PSRemoting</span></span>

## <span data-ttu-id="9aca9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9aca9-104">SYNOPSIS</span></span>
<span data-ttu-id="9aca9-105">Förhindrar att PowerShell-slutpunkter tar emot fjärr anslutningar.</span><span class="sxs-lookup"><span data-stu-id="9aca9-105">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="9aca9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9aca9-106">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9aca9-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9aca9-107">DESCRIPTION</span></span>

<span data-ttu-id="9aca9-108">`Disable-PSRemoting`Cmdleten blockerar fjärråtkomst till alla Windows PowerShell-sessionens slut punkts konfiguration på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-108">The `Disable-PSRemoting` cmdlet blocks remote access to all Windows PowerShell session endpoint configurations on the local computer.</span></span> <span data-ttu-id="9aca9-109">Detta inkluderar alla slut punkter som skapats av PowerShell 6 eller senare.</span><span class="sxs-lookup"><span data-stu-id="9aca9-109">This includes any endpoints created by PowerShell 6 or higher.</span></span>

<span data-ttu-id="9aca9-110">Använd cmdleten för att återaktivera fjärråtkomst till alla sessioner `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="9aca9-110">To re-enable remote access to all session configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="9aca9-111">Detta inkluderar alla slut punkter som skapats av PowerShell 6 eller senare.</span><span class="sxs-lookup"><span data-stu-id="9aca9-111">This includes any endpoints created by PowerShell 6 or higher.</span></span> <span data-ttu-id="9aca9-112">Använd parametern **AccessMode** för cmdleten om du vill aktivera fjärråtkomst till valda sessionsbaserade konfigurationer `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="9aca9-112">To enable remote access to selected session configurations, use the **AccessMode** parameter of the `Set-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="9aca9-113">Du kan också använda `Enable-PSSessionConfiguration` `Disable-PSSessionConfiguration` cmdletarna och för att aktivera och inaktivera sessionsinställningar för alla användare.</span><span class="sxs-lookup"><span data-stu-id="9aca9-113">You can also use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets to enable and disable session configurations for all users.</span></span> <span data-ttu-id="9aca9-114">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="9aca9-114">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9aca9-115">Trots att `Disable-PSRemoting` du har kört kan du fortfarande göra loopback-anslutningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-115">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="9aca9-116">En loopback-anslutning är en PowerShell-fjärrsession som kommer från och ansluter till samma lokala dator.</span><span class="sxs-lookup"><span data-stu-id="9aca9-116">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="9aca9-117">Fjärrsessioner från externa källor förblir blockerade.</span><span class="sxs-lookup"><span data-stu-id="9aca9-117">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="9aca9-118">För loopback-anslutningar måste du använda implicita autentiseringsuppgifter tillsammans med parametern **EnableNetworkAccess** .</span><span class="sxs-lookup"><span data-stu-id="9aca9-118">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="9aca9-119">Mer information om loopback-anslutningar finns i [New-PSSession](New-PSSession.md).</span><span class="sxs-lookup"><span data-stu-id="9aca9-119">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="9aca9-120">Om du vill köra den här cmdleten startar du Windows PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="9aca9-120">To run this cmdlet, start Windows PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="9aca9-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9aca9-121">EXAMPLES</span></span>

### <span data-ttu-id="9aca9-122">Exempel 1: förhindra fjärråtkomst till alla konfigurationer av sessioner</span><span class="sxs-lookup"><span data-stu-id="9aca9-122">Example 1: Prevent remote access to all session configurations</span></span>

<span data-ttu-id="9aca9-123">Det här exemplet förhindrar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-123">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="9aca9-124">Exempel 2: förhindra fjärråtkomst till alla datorkonfigurationer utan bekräftelse meddelande</span><span class="sxs-lookup"><span data-stu-id="9aca9-124">Example 2: Prevent remote access to all session configurations without confirmation prompt</span></span>

<span data-ttu-id="9aca9-125">Det här exemplet förhindrar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn utan att du behöver ange något.</span><span class="sxs-lookup"><span data-stu-id="9aca9-125">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="9aca9-126">Exempel 3: effekterna av att köra denna cmdlet</span><span class="sxs-lookup"><span data-stu-id="9aca9-126">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="9aca9-127">I det här exemplet visas effekterna av att använda `Disable-PSRemoting` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9aca9-127">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="9aca9-128">Starta PowerShell med alternativet **Kör som administratör** för att köra den här kommando sekvensen.</span><span class="sxs-lookup"><span data-stu-id="9aca9-128">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="9aca9-129">När du har inaktiverat sessionerna `New-PSSession` försöker cmdleten skapa en fjärrsession till den lokala datorn (kallas även "loopback").</span><span class="sxs-lookup"><span data-stu-id="9aca9-129">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="9aca9-130">Eftersom fjärråtkomst är inaktive rad på den lokala datorn Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="9aca9-130">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
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

### <span data-ttu-id="9aca9-131">Exempel 4: effekterna av att köra denna cmdlet och Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="9aca9-131">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="9aca9-132">I det här exemplet visas effekterna av sessionens konfigurationer av med hjälp av `Disable-PSRemoting` `Enable-PSRemoting` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="9aca9-132">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="9aca9-133">`Disable-PSRemoting` används för att inaktivera fjärråtkomst till alla PowerShell-sessioner för slut punkts konfiguration.</span><span class="sxs-lookup"><span data-stu-id="9aca9-133">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="9aca9-134">Parametern **Force** förhindrar alla användar meddelanden.</span><span class="sxs-lookup"><span data-stu-id="9aca9-134">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="9aca9-135">`Get-PSSessionConfiguration` `Format-Table` Cmdletarna och visar sessionens konfigurationer på datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-135">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="9aca9-136">Utdata visar att alla fjärran vändare med en nätverks-token nekas åtkomst till slut punkts konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="9aca9-136">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="9aca9-137">Gruppen Administratörer på den lokala datorn får åtkomst till slut punkts konfigurationerna så länge de ansluter lokalt (kallas även loopback) och använder implicita autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="9aca9-137">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow BUILTIN\Administrators AccessAllowed
microsoft.powershell32        BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="9aca9-138">`Enable-PSRemoting`Cmdleten återaktiverar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-138">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="9aca9-139">**Force** -parametern utelämnar alla användar meddelanden och startar om WinRM-tjänsten utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="9aca9-139">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="9aca9-140">De nya utdata visar att **AccessDenied** säkerhets beskrivningar har tagits bort från alla sessionsinställningar.</span><span class="sxs-lookup"><span data-stu-id="9aca9-140">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="9aca9-141">Exempel 5: loopback-anslutningar med inaktiverade sessioner med slut punkts konfiguration</span><span class="sxs-lookup"><span data-stu-id="9aca9-141">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="9aca9-142">Det här exemplet visar hur slut punkts konfigurationen är inaktive rad och hur du gör en lyckad loopback-anslutning till en inaktive rad slut punkt.</span><span class="sxs-lookup"><span data-stu-id="9aca9-142">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="9aca9-143">`Disable-PSRemoting` inaktiverar alla slut punkts konfigurationer för PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="9aca9-143">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message : Access is
denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [New-PSSession], PSRemotin
   gTransportException
    + FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed

```

```powershell
New-PSSession -ComputerName localhost -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="9aca9-144">Den första användningen av `New-PSSession` försök att skapa en fjärrsession till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-144">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="9aca9-145">Den här typen av anslutning går igenom nätverks stacken och är inte en loopback.</span><span class="sxs-lookup"><span data-stu-id="9aca9-145">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="9aca9-146">Det innebär att anslutnings försöket till den inaktiverade slut punkten Miss lyckas med fel meddelandet **åtkomst nekas** .</span><span class="sxs-lookup"><span data-stu-id="9aca9-146">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="9aca9-147">Den andra användningen av `New-PSSession` försöker också att skapa en fjärrsession till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-147">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="9aca9-148">I det här fallet lyckas det eftersom det är en loopback-anslutning som kringgår nätverks stacken.</span><span class="sxs-lookup"><span data-stu-id="9aca9-148">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="9aca9-149">En loopback-anslutning skapas när följande villkor uppfylls:</span><span class="sxs-lookup"><span data-stu-id="9aca9-149">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="9aca9-150">Dator namnet som ska anslutas till är localhost.</span><span class="sxs-lookup"><span data-stu-id="9aca9-150">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="9aca9-151">Inga autentiseringsuppgifter har skickats.</span><span class="sxs-lookup"><span data-stu-id="9aca9-151">No credentials are passed in.</span></span> <span data-ttu-id="9aca9-152">Den aktuella inloggade användaren (implicita autentiseringsuppgifter) används för anslutningen.</span><span class="sxs-lookup"><span data-stu-id="9aca9-152">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="9aca9-153">Växel parametern **EnableNetworkAccess** används.</span><span class="sxs-lookup"><span data-stu-id="9aca9-153">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="9aca9-154">Mer information om loopback-anslutningar finns i [New-PSSession](New-PSSession.md) Document.</span><span class="sxs-lookup"><span data-stu-id="9aca9-154">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="9aca9-155">Exempel 6: förhindra fjärråtkomst till sessionsinställningar som har anpassade säkerhets beskrivningar</span><span class="sxs-lookup"><span data-stu-id="9aca9-155">Example 6: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="9aca9-156">Det här exemplet visar att- `Disable-PSRemoting` cmdleten inaktiverar fjärråtkomst till alla sessionsinställningar som innehåller konfigurationer med anpassade säkerhets beskrivningar.</span><span class="sxs-lookup"><span data-stu-id="9aca9-156">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="9aca9-157">`Register-PSSessionConfiguration`skapar en **Test** testsessions-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="9aca9-157">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="9aca9-158">Parametern **sökväg** anger en konfigurations fil för sessionen som anpassar sessionen.</span><span class="sxs-lookup"><span data-stu-id="9aca9-158">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="9aca9-159">Parametern **ShowSecurityDescriptorUI** visar en dialog ruta som anger behörigheter för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="9aca9-159">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="9aca9-160">I dialog rutan behörigheter skapar vi anpassade fullständiga åtkomst behörigheter för den angivna användaren.</span><span class="sxs-lookup"><span data-stu-id="9aca9-160">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="9aca9-161">`Get-PSSessionConfiguration` `Format-Table` Cmdletarna och visar sessionens konfigurationer och deras egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9aca9-161">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="9aca9-162">Utdata visar att **testsessionens** konfiguration tillåter interaktiv åtkomst och särskilda behörigheter för den angivna användaren.</span><span class="sxs-lookup"><span data-stu-id="9aca9-162">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="9aca9-163">`Disable-PSRemoting` inaktiverar fjärråtkomst till alla konfigurationer för sessioner.</span><span class="sxs-lookup"><span data-stu-id="9aca9-163">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
DOMAIN01\User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\NETWORK AccessDenied, NTAUTHORITY\INTERACTIVE AccessAllowed,
BUILTIN\Administrators AccessAllowed, DOMAIN01\User01 AccessAllowed


[Server01] Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Rem
ote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="9aca9-164">Nu `Get-PSSessionConfiguration` visar-och `Format-Table` -cmdletarna att en **AccessDenied** säkerhets beskrivning för alla nätverks användare läggs till i alla konfigurationer för sessioner, **Test** inklusive konfigurationen för testsession.</span><span class="sxs-lookup"><span data-stu-id="9aca9-164">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="9aca9-165">Även om de andra säkerhets beskrivarna inte ändras har säkerhets beskrivningen "network_deny_all" företräde.</span><span class="sxs-lookup"><span data-stu-id="9aca9-165">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="9aca9-166">Detta illustreras med det försök att använda `New-PSSession` för att ansluta till **Test** konfigurationen av Testsessionen.</span><span class="sxs-lookup"><span data-stu-id="9aca9-166">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="9aca9-167">Exempel 7: återaktivera fjärråtkomst till valda sessionsbaserade</span><span class="sxs-lookup"><span data-stu-id="9aca9-167">Example 7: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="9aca9-168">Det här exemplet visar hur du återaktiverar fjärråtkomst enbart till valda sessionsinställningar.</span><span class="sxs-lookup"><span data-stu-id="9aca9-168">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="9aca9-169">När du har inaktiverat alla sessionsinställningar, återaktivera vi en speciell session.</span><span class="sxs-lookup"><span data-stu-id="9aca9-169">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="9aca9-170">`Set-PSSessionConfiguration`Cmdleten används för att ändra **Microsoft.** Konfiguration av servermanager-session.</span><span class="sxs-lookup"><span data-stu-id="9aca9-170">The `Set-PSSessionConfiguration` cmdlet is used to change the **microsoft.ServerManager** session configuration.</span></span> <span data-ttu-id="9aca9-171">Parametern **AccessMode** med värdet **fjärran sluten** för fjärråtkomst återaktiverar fjärråtkomst till konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="9aca9-171">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name Microsoft.ServerManager -AccessMode Remote -Force
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

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
```

## <span data-ttu-id="9aca9-172">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9aca9-172">PARAMETERS</span></span>

### <span data-ttu-id="9aca9-173">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9aca9-173">-Confirm</span></span>

<span data-ttu-id="9aca9-174">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9aca9-174">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9aca9-175">-Force</span><span class="sxs-lookup"><span data-stu-id="9aca9-175">-Force</span></span>
<span data-ttu-id="9aca9-176">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="9aca9-176">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="9aca9-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9aca9-177">-WhatIf</span></span>

<span data-ttu-id="9aca9-178">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="9aca9-178">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9aca9-179">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="9aca9-179">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9aca9-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9aca9-180">CommonParameters</span></span>

<span data-ttu-id="9aca9-181">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9aca9-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9aca9-182">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9aca9-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9aca9-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="9aca9-183">INPUTS</span></span>

### <span data-ttu-id="9aca9-184">Inget</span><span class="sxs-lookup"><span data-stu-id="9aca9-184">None</span></span>

<span data-ttu-id="9aca9-185">Det går inte att skicka några objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9aca9-185">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="9aca9-186">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9aca9-186">OUTPUTS</span></span>

### <span data-ttu-id="9aca9-187">Inget</span><span class="sxs-lookup"><span data-stu-id="9aca9-187">None</span></span>

<span data-ttu-id="9aca9-188">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="9aca9-188">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9aca9-189">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9aca9-189">NOTES</span></span>

- <span data-ttu-id="9aca9-190">Om du inaktiverar-sessionsinställningar återställs inte alla ändringar som har gjorts av `Enable-PSRemoting` `Enable-PSSessionConfiguration` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="9aca9-190">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="9aca9-191">Du kan behöva ångra följande ändringar manuellt.</span><span class="sxs-lookup"><span data-stu-id="9aca9-191">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="9aca9-192">Stoppa och inaktivera WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="9aca9-192">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="9aca9-193">Ta bort den lyssnare som accepterar begär Anden på alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="9aca9-193">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="9aca9-194">Inaktivera brand Väggs undantag för WS-Management kommunikation.</span><span class="sxs-lookup"><span data-stu-id="9aca9-194">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="9aca9-195">Återställ värdet för LocalAccountTokenFilterPolicy till 0, vilket begränsar fjärråtkomst till medlemmar i gruppen Administratörer på datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-195">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

  <span data-ttu-id="9aca9-196">En sessions konfiguration är en grupp med inställningar som definierar miljön för en session.</span><span class="sxs-lookup"><span data-stu-id="9aca9-196">A session configuration is a group of settings that define the environment for a session.</span></span> <span data-ttu-id="9aca9-197">Varje session som ansluter till datorn måste använda en av de sessionsbaserade som har registrerats på datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-197">Every session that connects to the computer must use one of the session configurations that are registered on the computer.</span></span> <span data-ttu-id="9aca9-198">Genom att neka fjärråtkomst till alla sessioner förhindrar du att fjärranslutna användare upprättar sessioner som ansluter till datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-198">By denying remote access to all session configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

  <span data-ttu-id="9aca9-199">I Windows PowerShell 2,0 `Disable-PSRemoting` lägger till en Deny_All post i säkerhets beskrivarna för alla konfigurationer av sessioner.</span><span class="sxs-lookup"><span data-stu-id="9aca9-199">In Windows PowerShell 2.0, `Disable-PSRemoting` adds a Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="9aca9-200">Den här inställningen förhindrar att alla användare skapar användar hanterade sessioner till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9aca9-200">This setting prevents all users from creating user-managed sessions to the local computer.</span></span> <span data-ttu-id="9aca9-201">I Windows PowerShell 3,0 `Disable-PSRemoting` lägger till en Network_Deny_All post i säkerhets beskrivarna för alla konfigurationer av sessioner.</span><span class="sxs-lookup"><span data-stu-id="9aca9-201">In Windows PowerShell 3.0, `Disable-PSRemoting` adds a Network_Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="9aca9-202">Den här inställningen förhindrar användare på andra datorer från att skapa användar hanterade sessioner på den lokala datorn, men tillåter användare av den lokala datorn att skapa användar hanterade loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="9aca9-202">This setting prevents users on other computers from creating user-managed sessions on the local computer, but allows users of the local computer to create user-managed loopback sessions.</span></span>

  <span data-ttu-id="9aca9-203">I Windows PowerShell 2,0 `Disable-PSRemoting` är motsvarigheten till `Disable-PSSessionConfiguration -Name *` .</span><span class="sxs-lookup"><span data-stu-id="9aca9-203">In Windows PowerShell 2.0, `Disable-PSRemoting` is the equivalent of `Disable-PSSessionConfiguration -Name *`.</span></span> <span data-ttu-id="9aca9-204">I Windows PowerShell 3,0 och senare versioner `Disable-PSRemoting` är motsvarigheten till `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span><span class="sxs-lookup"><span data-stu-id="9aca9-204">In Windows PowerShell 3.0 and later releases, `Disable-PSRemoting` is the equivalent of `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span></span>

## <span data-ttu-id="9aca9-205">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9aca9-205">RELATED LINKS</span></span>

[<span data-ttu-id="9aca9-206">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9aca9-206">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="9aca9-207">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="9aca9-207">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="9aca9-208">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9aca9-208">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="9aca9-209">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="9aca9-209">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="9aca9-210">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9aca9-210">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="9aca9-211">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9aca9-211">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="9aca9-212">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="9aca9-212">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="9aca9-213">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="9aca9-213">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
