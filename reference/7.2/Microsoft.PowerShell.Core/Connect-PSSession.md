---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: fda672ba4f6dafc9f955ef8025c386f7732d81bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709637"
---
# <span data-ttu-id="4f575-102">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-102">Connect-PSSession</span></span>

## <span data-ttu-id="4f575-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4f575-103">SYNOPSIS</span></span>
<span data-ttu-id="4f575-104">Återansluter till frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="4f575-104">Reconnects to disconnected sessions.</span></span>

## <span data-ttu-id="4f575-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f575-105">SYNTAX</span></span>

### <span data-ttu-id="4f575-106">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="4f575-106">Name (Default)</span></span>

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f575-107">Session</span><span class="sxs-lookup"><span data-stu-id="4f575-107">Session</span></span>

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f575-108">ComputerNameGuid</span><span class="sxs-lookup"><span data-stu-id="4f575-108">ComputerNameGuid</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f575-109">ComputerName</span><span class="sxs-lookup"><span data-stu-id="4f575-109">ComputerName</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f575-110">ConnectionUriGuid</span><span class="sxs-lookup"><span data-stu-id="4f575-110">ConnectionUriGuid</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f575-111">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="4f575-111">ConnectionUri</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f575-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4f575-112">InstanceId</span></span>

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f575-113">Id</span><span class="sxs-lookup"><span data-stu-id="4f575-113">Id</span></span>

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4f575-114">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4f575-114">DESCRIPTION</span></span>

<span data-ttu-id="4f575-115">`Connect-PSSession`Cmdleten återansluter till användarens hanterade PowerShell-sessioner (**PSSessions**) som kopplades från.</span><span class="sxs-lookup"><span data-stu-id="4f575-115">The `Connect-PSSession` cmdlet reconnects to user-managed PowerShell sessions (**PSSessions**) that were disconnected.</span></span> <span data-ttu-id="4f575-116">Den fungerar på sessioner som är frånkopplade, till exempel med hjälp av `Disconnect-PSSession` cmdleten eller parametern **InDisconnectedSession** i `Invoke-Command` cmdleten, och de som frånkopplats oavsiktligt, till exempel vid ett tillfälligt nätverks avbrott.</span><span class="sxs-lookup"><span data-stu-id="4f575-116">It works on sessions that are disconnected intentionally, such as by using the `Disconnect-PSSession` cmdlet or the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet, and those that were disconnected unintentionally, such as by a temporary network outage.</span></span>

<span data-ttu-id="4f575-117">`Connect-PSSession` kan ansluta till en frånkopplad session som har startats av samma användare.</span><span class="sxs-lookup"><span data-stu-id="4f575-117">`Connect-PSSession` can connect to any disconnected session that was started by the same user.</span></span> <span data-ttu-id="4f575-118">Detta inkluderar de som startades av eller frånkopplats från andra sessioner på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="4f575-118">These include those that were started by or disconnected from other sessions on other computers.</span></span>

<span data-ttu-id="4f575-119">`Connect-PSSession`Det går dock inte att ansluta till brutna eller stängda sessioner eller interaktiva sessioner som startats med hjälp av `Enter-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4f575-119">However, `Connect-PSSession` cannot connect to broken or closed sessions, or interactive sessions started by using the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="4f575-120">Du kan inte heller ansluta sessioner till sessioner som har startats av andra användare, om du inte kan ange autentiseringsuppgifterna för den användare som skapade sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-120">Also you cannot connect sessions to sessions started by other users, unless you can provide the credentials of the user who created the session.</span></span>

<span data-ttu-id="4f575-121">Mer information om funktionen frånkopplade sessioner finns [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span><span class="sxs-lookup"><span data-stu-id="4f575-121">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="4f575-122">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4f575-122">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="4f575-123">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4f575-123">EXAMPLES</span></span>

### <span data-ttu-id="4f575-124">Exempel 1: Återanslut till en session</span><span class="sxs-lookup"><span data-stu-id="4f575-124">Example 1: Reconnect to a session</span></span>

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

<span data-ttu-id="4f575-125">Det här kommandot återansluter till ITTask-sessionen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="4f575-125">This command reconnects to the ITTask session on the Server01 computer.</span></span>

<span data-ttu-id="4f575-126">Resultatet visar att kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="4f575-126">The output shows that the command was successful.</span></span> <span data-ttu-id="4f575-127">Sessionens **tillstånd** öppnas och **tillgängligheten** är tillgänglig, vilket innebär att du kan köra kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-127">The **State** of the session is Opened and the **Availability** is Available, which indicates that you can run commands in the session.</span></span>

### <span data-ttu-id="4f575-128">Exempel 2: påverkan från från koppling och åter anslutning</span><span class="sxs-lookup"><span data-stu-id="4f575-128">Example 2: Effect of disconnecting and reconnecting</span></span>

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

<span data-ttu-id="4f575-129">Det här exemplet visar hur du kopplar från och sedan återansluter till en session.</span><span class="sxs-lookup"><span data-stu-id="4f575-129">This example shows the effect of disconnecting and then reconnecting to a session.</span></span>

<span data-ttu-id="4f575-130">Det första kommandot använder `Get-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4f575-130">The first command uses the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="4f575-131">Utan parametern **computername** , hämtar kommandot endast sessioner som har skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-131">Without the **ComputerName** parameter, the command gets only sessions that were created in the current session.</span></span>

<span data-ttu-id="4f575-132">Utdata visar att kommandot hämtar sessionen för säkerhets kopiering på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4f575-132">The output shows that the command gets the Backups session on the local computer.</span></span> <span data-ttu-id="4f575-133">Sessionens **tillstånd** öppnas **och tillgängligheten är tillgänglig** .</span><span class="sxs-lookup"><span data-stu-id="4f575-133">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="4f575-134">Det andra kommandot använder `Get-PSSession` cmdleten för att hämta **PSSession** -objekt som skapades i den aktuella sessionen och `Disconnect-PSSession` cmdleten för att koppla från sessionerna.</span><span class="sxs-lookup"><span data-stu-id="4f575-134">The second command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Disconnect-PSSession` cmdlet to disconnect the sessions.</span></span> <span data-ttu-id="4f575-135">Utdata visar att säkerhets kopierings sessionen kopplades från.</span><span class="sxs-lookup"><span data-stu-id="4f575-135">The output shows that the Backups session was disconnected.</span></span> <span data-ttu-id="4f575-136">Sessionens **status** är frånkopplad och **tillgängligheten** är ingen.</span><span class="sxs-lookup"><span data-stu-id="4f575-136">The **State** of the session is Disconnected and the **Availability** is None.</span></span>

<span data-ttu-id="4f575-137">Det tredje kommandot använder `Get-PSSession` cmdleten för att hämta **PSSession** -objekt som skapades i den aktuella sessionen och `Connect-PSSession` cmdleten för att återansluta sessionerna.</span><span class="sxs-lookup"><span data-stu-id="4f575-137">The third command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Connect-PSSession` cmdlet to reconnect the sessions.</span></span> <span data-ttu-id="4f575-138">Utdata visar att säkerhets kopierings sessionen har återanslutits.</span><span class="sxs-lookup"><span data-stu-id="4f575-138">The output shows that the Backups session was reconnected.</span></span> <span data-ttu-id="4f575-139">Sessionens **tillstånd** öppnas **och tillgängligheten är tillgänglig** .</span><span class="sxs-lookup"><span data-stu-id="4f575-139">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="4f575-140">Om du använder `Connect-PSSession` cmdleten på en-session som inte är frånkopplad, påverkar inte-sessionen sessionen och genererar inga fel.</span><span class="sxs-lookup"><span data-stu-id="4f575-140">If you use the `Connect-PSSession` cmdlet on a session that is not disconnected, the command does not affect the session and it does not generate any errors.</span></span>

### <span data-ttu-id="4f575-141">Exempel 3: serie kommandon i ett företags scenario</span><span class="sxs-lookup"><span data-stu-id="4f575-141">Example 3: Series of commands in an enterprise scenario</span></span>

<span data-ttu-id="4f575-142">Den här serien med kommandon visar hur `Connect-PSSession` cmdleten kan användas i ett företags scenario.</span><span class="sxs-lookup"><span data-stu-id="4f575-142">This series of commands shows how the `Connect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="4f575-143">I det här fallet startar en system administratör ett långvarigt jobb i en session på en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="4f575-143">In this case, a system administrator starts a long-running job in a session on a remote computer.</span></span> <span data-ttu-id="4f575-144">När jobbet har startats kopplas administratören bort från sessionen och går sedan hemma.</span><span class="sxs-lookup"><span data-stu-id="4f575-144">After starting the job, the administrator disconnects from the session and goes home.</span></span>
<span data-ttu-id="4f575-145">Senare på kvällen loggar administratören in på sin hem dator och kontrollerar att jobbet kördes tills det har slutförts.</span><span class="sxs-lookup"><span data-stu-id="4f575-145">Later that evening, the administrator logs on to her home computer and verifies that the job ran until it is completed.</span></span>

<span data-ttu-id="4f575-146">Administratören börjar genom att skapa en session på en fjärrdator och köra ett skript i sessionen. Det första kommandot använder `New-PSSession` cmdleten för att skapa ITTask-sessionen på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="4f575-146">The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 remote computer.</span></span> <span data-ttu-id="4f575-147">Kommandot använder parametern **ConfigurationName** för att ange konfigurationen av ITTasks-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-147">The command uses the **ConfigurationName** parameter to specify the ITTasks session configuration.</span></span> <span data-ttu-id="4f575-148">Kommandot sparar sessionerna i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4f575-148">The command saves the sessions in the `$s` variable.</span></span>

<span data-ttu-id="4f575-149">Den andra kommando- `Invoke-Command` cmdleten för att starta ett bakgrunds jobb i sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4f575-149">The second command `Invoke-Command` cmdlet to start a background job in the session in the `$s` variable.</span></span> <span data-ttu-id="4f575-150">Den använder parametern **sökväg** för att köra skriptet i bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="4f575-150">It uses the **FilePath** parameter to run the script in the background job.</span></span>

<span data-ttu-id="4f575-151">Det tredje kommandot använder `Disconnect-PSSession` cmdleten för att koppla från sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4f575-151">The third command uses the `Disconnect-PSSession` cmdlet to disconnect from the session in the `$s` variable.</span></span> <span data-ttu-id="4f575-152">Kommandot använder parametern **OutputBufferingMode** med värdet drop för att förhindra att skriptet blockeras genom att skicka utdata till sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-152">The command uses the **OutputBufferingMode** parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session.</span></span> <span data-ttu-id="4f575-153">Den använder parametern **IdleTimeoutSec** för att förlänga tids gränsen för sessionen till 15 timmar.</span><span class="sxs-lookup"><span data-stu-id="4f575-153">It uses the **IdleTimeoutSec** parameter to extend the session time-out to 15 hours.</span></span> <span data-ttu-id="4f575-154">När kommandot har slutförts låser administratören sin dator och går hem för kvälls tid.</span><span class="sxs-lookup"><span data-stu-id="4f575-154">When the command is completed, the administrator locks her computer and goes home for the evening.</span></span>

<span data-ttu-id="4f575-155">Senare på kvällen startar administratören sin hem dator, loggar in på företags nätverket och startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f575-155">Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell.</span></span> <span data-ttu-id="4f575-156">Det fjärde kommandot använder `Get-PSSession` cmdleten för att hämta sessionerna på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="4f575-156">The fourth command uses the `Get-PSSession` cmdlet to get the sessions on the Server01 computer.</span></span> <span data-ttu-id="4f575-157">Kommandot hittar ITTask-sessionen. Det femte kommandot använder `Connect-PSSession` cmdleten för att ansluta till ITTask-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-157">The command finds the ITTask session.The fifth command uses the `Connect-PSSession` cmdlet to connect to the ITTask session.</span></span> <span data-ttu-id="4f575-158">Kommandot sparar sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4f575-158">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="4f575-159">Det sjätte kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-Job` kommando i sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4f575-159">The sixth command uses the `Invoke-Command` cmdlet to run a `Get-Job` command in the session in the `$s` variable.</span></span> <span data-ttu-id="4f575-160">Resultatet visar att jobbet har slutförts. Det sjunde kommandot använder `Invoke-Command` cmdleten för att köra ett `Receive-Job` kommando i sessionen i `$s` variabeln i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-160">The output shows that the job finished successfully.The seventh command uses the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session in the `$s` variable in the session.</span></span> <span data-ttu-id="4f575-161">Kommandot sparar resultatet i `$BackupSpecs` variabeln. Det åttonde kommandot använder `Invoke-Command` cmdleten för att köra ett annat skript i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-161">The command saves the results in the `$BackupSpecs` variable.The eighth command uses the `Invoke-Command` cmdlet to runs another script in the session.</span></span> <span data-ttu-id="4f575-162">Kommandot använder värdet för `$BackupSpecs` variabeln i sessionen som indatamängden för skriptet.</span><span class="sxs-lookup"><span data-stu-id="4f575-162">The command uses the value of the `$BackupSpecs` variable in the session as input to the script.</span></span>

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

<span data-ttu-id="4f575-163">Det nionde kommandot kopplar från sessionen i `$s` variabeln. Administratören stänger PowerShell och stänger datorn.</span><span class="sxs-lookup"><span data-stu-id="4f575-163">The ninth command disconnects from the session in the `$s` variable.The administrator closes PowerShell and closes the computer.</span></span> <span data-ttu-id="4f575-164">Hon kan återansluta till sessionen nästa dag och kontrol lera skript statusen från arbets datorn.</span><span class="sxs-lookup"><span data-stu-id="4f575-164">She can reconnect to the session on the next day and check the script status from her work computer.</span></span>

## <span data-ttu-id="4f575-165">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4f575-165">PARAMETERS</span></span>

### <span data-ttu-id="4f575-166">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="4f575-166">-AllowRedirection</span></span>

<span data-ttu-id="4f575-167">Anger att denna cmdlet tillåter omdirigering av anslutningen till en alternativ URI.</span><span class="sxs-lookup"><span data-stu-id="4f575-167">Indicates that this cmdlet allows redirection of this connection to an alternate URI.</span></span>

<span data-ttu-id="4f575-168">När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI.</span><span class="sxs-lookup"><span data-stu-id="4f575-168">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="4f575-169">Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern om du vill att den ska kunna omdirigera anslutningen.</span><span class="sxs-lookup"><span data-stu-id="4f575-169">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="4f575-170">Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session.</span><span class="sxs-lookup"><span data-stu-id="4f575-170">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="4f575-171">Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för variabeln **$PSSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="4f575-171">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="4f575-172">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="4f575-172">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-173">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="4f575-173">-ApplicationName</span></span>

<span data-ttu-id="4f575-174">Anger namnet på ett program.</span><span class="sxs-lookup"><span data-stu-id="4f575-174">Specifies the name of an application.</span></span> <span data-ttu-id="4f575-175">Denna cmdlet ansluter bara till sessioner som använder det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="4f575-175">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="4f575-176">Ange program namns segmentet för anslutnings-URI: n.</span><span class="sxs-lookup"><span data-stu-id="4f575-176">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="4f575-177">I följande anslutnings-URI är till exempel program namnet WSMan: `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="4f575-177">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="4f575-178">Program namnet för en session lagras i egenskapen **körnings utrymme. ConnectionInfo. APPNAME** för sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-178">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="4f575-179">Värdet för den här parametern används för att välja och filtrera sessioner.</span><span class="sxs-lookup"><span data-stu-id="4f575-179">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="4f575-180">Den ändrar inte det program som används av sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-180">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-181">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="4f575-181">-Authentication</span></span>

<span data-ttu-id="4f575-182">Anger den mekanism som används för att autentisera användarautentiseringsuppgifter i kommandot för att återansluta till den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-182">Specifies the mechanism that is used to authenticate user credentials in the command to reconnect to the disconnected session.</span></span> <span data-ttu-id="4f575-183">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4f575-183">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4f575-184">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="4f575-184">Default</span></span>
- <span data-ttu-id="4f575-185">Grundläggande</span><span class="sxs-lookup"><span data-stu-id="4f575-185">Basic</span></span>
- <span data-ttu-id="4f575-186">CredSSP</span><span class="sxs-lookup"><span data-stu-id="4f575-186">Credssp</span></span>
- <span data-ttu-id="4f575-187">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="4f575-187">Digest</span></span>
- <span data-ttu-id="4f575-188">Kerberos</span><span class="sxs-lookup"><span data-stu-id="4f575-188">Kerberos</span></span>
- <span data-ttu-id="4f575-189">Negotiate</span><span class="sxs-lookup"><span data-stu-id="4f575-189">Negotiate</span></span>
- <span data-ttu-id="4f575-190">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="4f575-190">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="4f575-191">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="4f575-191">The default value is Default.</span></span>

<span data-ttu-id="4f575-192">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="4f575-192">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="4f575-193">CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="4f575-193">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="4f575-194">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="4f575-194">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="4f575-195">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-195">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-196">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="4f575-196">-CertificateThumbprint</span></span>

<span data-ttu-id="4f575-197">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att ansluta till den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-197">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="4f575-198">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="4f575-198">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="4f575-199">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="4f575-199">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="4f575-200">De kan endast mappas till lokala användar konton.</span><span class="sxs-lookup"><span data-stu-id="4f575-200">They can be mapped only to local user accounts.</span></span> <span data-ttu-id="4f575-201">De fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="4f575-201">They do not work with domain accounts.</span></span>

<span data-ttu-id="4f575-202">Om du vill hämta ett tumavtryck för certifikatet använder du ett `Get-Item` eller- `Get-ChildItem` kommando i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="4f575-202">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-203">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4f575-203">-ComputerName</span></span>

<span data-ttu-id="4f575-204">Anger de datorer där de frånkopplade sessionerna lagras.</span><span class="sxs-lookup"><span data-stu-id="4f575-204">Specifies the computers on which the disconnected sessions are stored.</span></span> <span data-ttu-id="4f575-205">Sessioner lagras på den dator som finns på Server sidan eller tar emot en anslutning.</span><span class="sxs-lookup"><span data-stu-id="4f575-205">Sessions are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="4f575-206">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4f575-206">The default is the local computer.</span></span>

<span data-ttu-id="4f575-207">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en dator.</span><span class="sxs-lookup"><span data-stu-id="4f575-207">Type the NetBIOS name, an IP address, or a fully qualified domain name of one computer.</span></span> <span data-ttu-id="4f575-208">Jokertecken tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="4f575-208">Wildcard characters are not permitted.</span></span> <span data-ttu-id="4f575-209">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.)</span><span class="sxs-lookup"><span data-stu-id="4f575-209">To specify the local computer, type the computer name, localhost, or a dot (.)</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameGuid, ComputerName
Aliases: Cn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-210">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="4f575-210">-ConfigurationName</span></span>

<span data-ttu-id="4f575-211">Ansluter endast till sessioner som använder den angivna konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4f575-211">Connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="4f575-212">Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-212">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="4f575-213">Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="4f575-213">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="4f575-214">Konfigurations namnet för en session lagras i sessionens **ConfigurationName** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="4f575-214">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="4f575-215">Värdet för den här parametern används för att välja och filtrera sessioner.</span><span class="sxs-lookup"><span data-stu-id="4f575-215">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="4f575-216">Den ändrar inte den sessionsinformation som sessionen använder.</span><span class="sxs-lookup"><span data-stu-id="4f575-216">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="4f575-217">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="4f575-217">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-218">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="4f575-218">-ConnectionUri</span></span>

<span data-ttu-id="4f575-219">Anger URI: erna för anslutningens slut punkter för de frånkopplade sessionerna.</span><span class="sxs-lookup"><span data-stu-id="4f575-219">Specifies the URIs of the connection endpoints for the disconnected sessions.</span></span>

<span data-ttu-id="4f575-220">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="4f575-220">The URI must be fully qualified.</span></span> <span data-ttu-id="4f575-221">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="4f575-221">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="4f575-222">Standardvärdet är följande:</span><span class="sxs-lookup"><span data-stu-id="4f575-222">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="4f575-223">Om du inte anger en anslutnings-URI kan du använda parametrarna **UseSSL** och **port** för att ange anslutnings-URI-värden.</span><span class="sxs-lookup"><span data-stu-id="4f575-223">If you do not specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="4f575-224">Giltiga värden för URI: n i **transport** segmentet är http och https.</span><span class="sxs-lookup"><span data-stu-id="4f575-224">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="4f575-225">Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4f575-225">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="4f575-226">Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4f575-226">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="4f575-227">Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="4f575-227">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-228">-Credential</span><span class="sxs-lookup"><span data-stu-id="4f575-228">-Credential</span></span>

<span data-ttu-id="4f575-229">Anger ett användar konto som har behörighet att ansluta till den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-229">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="4f575-230">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="4f575-230">The default is the current user.</span></span>

<span data-ttu-id="4f575-231">Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett `PSCredential` objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4f575-231">Type a user name, such as `User01` or `Domain01\User01`, or enter a `PSCredential` object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="4f575-232">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="4f575-232">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="4f575-233">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="4f575-233">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="4f575-234">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="4f575-234">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-235">-ID</span><span class="sxs-lookup"><span data-stu-id="4f575-235">-Id</span></span>

<span data-ttu-id="4f575-236">Anger ID: n för de frånkopplade sessionerna.</span><span class="sxs-lookup"><span data-stu-id="4f575-236">Specifies the IDs of the disconnected sessions.</span></span> <span data-ttu-id="4f575-237">**ID-** parametern fungerar bara när den frånkopplade sessionen tidigare var ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-237">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="4f575-238">Den här parametern är giltig, men inte effektiv, när sessionen lagras på den lokala datorn, men inte var ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-238">This parameter is valid, but not effective, when the session is stored on the local computer, but was not connected to the current session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-239">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="4f575-239">-InstanceId</span></span>

<span data-ttu-id="4f575-240">Anger instans-ID: n för de frånkopplade sessionerna.</span><span class="sxs-lookup"><span data-stu-id="4f575-240">Specifies the instance IDs of the disconnected sessions.</span></span>

<span data-ttu-id="4f575-241">Instans-ID är ett GUID som unikt identifierar en **PSSession** på en lokal eller fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="4f575-241">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span>

<span data-ttu-id="4f575-242">Instans-ID: t lagras i egenskapen **InstanceID** i **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="4f575-242">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-243">-Name</span><span class="sxs-lookup"><span data-stu-id="4f575-243">-Name</span></span>

<span data-ttu-id="4f575-244">Anger de egna namnen på de frånkopplade sessionerna.</span><span class="sxs-lookup"><span data-stu-id="4f575-244">Specifies the friendly names of the disconnected sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-245">-Port</span><span class="sxs-lookup"><span data-stu-id="4f575-245">-Port</span></span>

<span data-ttu-id="4f575-246">Anger nätverks porten på den fjärrdator som används för att återansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-246">Specifies the network port on the remote computer that is used to reconnect to the session.</span></span> <span data-ttu-id="4f575-247">Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="4f575-247">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="4f575-248">Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4f575-248">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="4f575-249">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="4f575-249">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="4f575-250">Konfigurera lyssnaren genom att skriva följande två kommandon i PowerShell-prompten:</span><span class="sxs-lookup"><span data-stu-id="4f575-250">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="4f575-251">Använd inte **port** parametern om du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="4f575-251">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="4f575-252">Porten som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="4f575-252">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="4f575-253">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="4f575-253">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-254">– Session</span><span class="sxs-lookup"><span data-stu-id="4f575-254">-Session</span></span>

<span data-ttu-id="4f575-255">Anger de frånkopplade sessionerna.</span><span class="sxs-lookup"><span data-stu-id="4f575-255">Specifies the disconnected sessions.</span></span> <span data-ttu-id="4f575-256">Ange en variabel som innehåller **PSSession** -objekt eller ett kommando som skapar eller hämtar **PSSession** -objekt, till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="4f575-256">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-257">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="4f575-257">-SessionOption</span></span>

<span data-ttu-id="4f575-258">Anger avancerade alternativ för sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-258">Specifies advanced options for the session.</span></span> <span data-ttu-id="4f575-259">Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.</span><span class="sxs-lookup"><span data-stu-id="4f575-259">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="4f575-260">Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="4f575-260">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="4f575-261">Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-261">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="4f575-262">Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-262">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="4f575-263">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-263">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="4f575-264">En beskrivning av de sessionsinformation som innehåller standardvärdena finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="4f575-264">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="4f575-265">Information om variabeln **$PSSessionOption** finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="4f575-265">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="4f575-266">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="4f575-266">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-267">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="4f575-267">-ThrottleLimit</span></span>

<span data-ttu-id="4f575-268">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="4f575-268">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="4f575-269">Om du utelämnar den här parametern eller anger värdet 0, används standardvärdet 32.</span><span class="sxs-lookup"><span data-stu-id="4f575-269">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="4f575-270">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="4f575-270">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-271">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="4f575-271">-UseSSL</span></span>

<span data-ttu-id="4f575-272">Anger att denna cmdlet använder Secure Sockets Layer (SSL)-protokollet för att ansluta till den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-272">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="4f575-273">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="4f575-273">By default, SSL is not used.</span></span>

<span data-ttu-id="4f575-274">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="4f575-274">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="4f575-275">Parametern **UseSSL** är ett ytterligare skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="4f575-275">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="4f575-276">Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="4f575-276">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f575-277">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4f575-277">-Confirm</span></span>

<span data-ttu-id="4f575-278">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4f575-278">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4f575-279">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4f575-279">-WhatIf</span></span>

<span data-ttu-id="4f575-280">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="4f575-280">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4f575-281">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="4f575-281">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4f575-282">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f575-282">CommonParameters</span></span>

<span data-ttu-id="4f575-283">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f575-283">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f575-284">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4f575-284">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f575-285">INDATA</span><span class="sxs-lookup"><span data-stu-id="4f575-285">INPUTS</span></span>

### <span data-ttu-id="4f575-286">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-286">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="4f575-287">Du kan skicka en session (**PSSession**) till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f575-287">You can pipe a session (**PSSession**) to this cmdlet.</span></span>

## <span data-ttu-id="4f575-288">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4f575-288">OUTPUTS</span></span>

### <span data-ttu-id="4f575-289">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-289">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="4f575-290">Den här cmdleten returnerar ett objekt som representerar den session som den återanslutet till.</span><span class="sxs-lookup"><span data-stu-id="4f575-290">This cmdlet returns an object that represents the session to which it reconnected.</span></span>

## <span data-ttu-id="4f575-291">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4f575-291">NOTES</span></span>

- <span data-ttu-id="4f575-292">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="4f575-292">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="4f575-293">`Connect-PSSession` återansluter endast till sessioner som är frånkopplade, det vill säga sessioner som har värdet frånkopplat för egenskapen **State** .</span><span class="sxs-lookup"><span data-stu-id="4f575-293">`Connect-PSSession` reconnects only to sessions that are disconnected, that is, sessions that have a value of Disconnected for the **State** property.</span></span> <span data-ttu-id="4f575-294">Endast sessioner som är anslutna till, eller slutar på, datorer som kör Windows PowerShell 3,0 eller senare versioner kan kopplas från och återanslutas.</span><span class="sxs-lookup"><span data-stu-id="4f575-294">Only sessions that are connected to, or end at, computers that run Windows PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

- <span data-ttu-id="4f575-295">Om du använder `Connect-PSSession` på en-session som inte är frånkopplad, påverkar inte kommandot sessionen och genererar inte fel.</span><span class="sxs-lookup"><span data-stu-id="4f575-295">If you use `Connect-PSSession` on a session that is not disconnected, the command does not affect the session and it does not generate errors.</span></span>

- <span data-ttu-id="4f575-296">Frånkopplade loopback-sessioner med interaktiva tokens, som skapas med hjälp av parametern **EnableNetworkAccess** , kan bara återanslutas från den dator där sessionen skapades.</span><span class="sxs-lookup"><span data-stu-id="4f575-296">Disconnected loopback sessions with interactive tokens, which are created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="4f575-297">Den här begränsningen skyddar datorn från skadlig åtkomst.</span><span class="sxs-lookup"><span data-stu-id="4f575-297">This restriction protects the computer from malicious access.</span></span>

- <span data-ttu-id="4f575-298">Värdet för egenskapen **State** för en **PSSession** är i förhållande till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-298">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="4f575-299">Därför innebär värdet **frånkopplat** att **PSSession** inte är ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-299">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="4f575-300">Det innebär dock inte att **PSSession** är frånkopplad från alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="4f575-300">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="4f575-301">Den kan vara ansluten till en annan session.</span><span class="sxs-lookup"><span data-stu-id="4f575-301">It might be connected to a different session.</span></span> <span data-ttu-id="4f575-302">Använd egenskapen **tillgänglighet** för att avgöra om du kan ansluta eller återansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-302">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="4f575-303">**Tillgänglighet** svärdet none anger att du kan ansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-303">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="4f575-304">Värdet upptagen anger att du inte kan ansluta till **PSSession** eftersom det är anslutet till en annan session.</span><span class="sxs-lookup"><span data-stu-id="4f575-304">A value of Busy indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

  <span data-ttu-id="4f575-305">Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState-uppräkning](/dotnet/api/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="4f575-305">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="4f575-306">Mer information om värdena för egenskapen **Availability** för sessioner finns i [RunspaceAvailability-uppräkning](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="4f575-306">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

- <span data-ttu-id="4f575-307">Du kan inte ändra timeout-värdet för inaktivitet för en **PSSession** när du ansluter till **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="4f575-307">You cannot change the idle time-out value of a **PSSession** when you connect to the **PSSession**.</span></span> <span data-ttu-id="4f575-308">Parametern **SessionOption** för `Connect-PSSession` använder ett **SessionOption** -objekt som har ett **idleTimeout** -värde.</span><span class="sxs-lookup"><span data-stu-id="4f575-308">The **SessionOption** parameter of `Connect-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="4f575-309">Men **idleTimeout** -värdet för **SessionOption** -objektet och variabeln **idleTimeout** `$PSSessionOption` ignoreras vid anslutning till en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="4f575-309">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when connecting to a **PSSession**.</span></span>

  <span data-ttu-id="4f575-310">Du kan ange och ändra tids gränsen för inaktivitet i en **PSSession** när du skapar **PSSession**, genom att använda `New-PSSession` `Invoke-Command` cmdletarna eller och när du kopplar bort från **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="4f575-310">You can set and change the idle time-out of a **PSSession** when you create the **PSSession**, by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>

  <span data-ttu-id="4f575-311">Egenskapen **idleTimeout** för en **PSSession** är viktig för frånkopplade sessioner, eftersom den fastställer hur länge en frånkopplad session ska behållas på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="4f575-311">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions, because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="4f575-312">Frånkopplade sessioner anses vara inaktiva från det ögonblick då de kopplas från, även om kommandon körs i den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="4f575-312">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

## <span data-ttu-id="4f575-313">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4f575-313">RELATED LINKS</span></span>

[<span data-ttu-id="4f575-314">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-314">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="4f575-315">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-315">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="4f575-316">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-316">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="4f575-317">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-317">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="4f575-318">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4f575-318">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="4f575-319">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-319">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="4f575-320">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="4f575-320">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="4f575-321">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="4f575-321">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="4f575-322">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-322">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="4f575-323">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4f575-323">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="4f575-324">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="4f575-324">Remove-PSSession</span></span>](Remove-PSSession.md)
