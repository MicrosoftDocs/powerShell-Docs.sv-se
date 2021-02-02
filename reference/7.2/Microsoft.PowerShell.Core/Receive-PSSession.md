---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 4bc7ba3a8129dd332b13bee30e386dd459d92226
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710464"
---
# <span data-ttu-id="771f5-102">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="771f5-102">Receive-PSSession</span></span>

## <span data-ttu-id="771f5-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="771f5-103">SYNOPSIS</span></span>

<span data-ttu-id="771f5-104">Hämtar resultat från kommandon i frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="771f5-104">Gets results of commands in disconnected sessions</span></span>

## <span data-ttu-id="771f5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="771f5-105">SYNTAX</span></span>

### <span data-ttu-id="771f5-106">Session (standard)</span><span class="sxs-lookup"><span data-stu-id="771f5-106">Session (Default)</span></span>

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="771f5-107">Id</span><span class="sxs-lookup"><span data-stu-id="771f5-107">Id</span></span>

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="771f5-108">ComputerSessionName</span><span class="sxs-lookup"><span data-stu-id="771f5-108">ComputerSessionName</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="771f5-109">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="771f5-109">ComputerInstanceId</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="771f5-110">ConnectionUriSessionName</span><span class="sxs-lookup"><span data-stu-id="771f5-110">ConnectionUriSessionName</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="771f5-111">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="771f5-111">ConnectionUriInstanceId</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="771f5-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="771f5-112">InstanceId</span></span>

```
Receive-PSSession -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="771f5-113">SessionName</span><span class="sxs-lookup"><span data-stu-id="771f5-113">SessionName</span></span>

```
Receive-PSSession -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="771f5-114">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="771f5-114">DESCRIPTION</span></span>

<span data-ttu-id="771f5-115">`Receive-PSSession`Cmdlet: en hämtar resultatet av kommandon som körs i PowerShell-sessioner (**PSSession**) som kopplades från.</span><span class="sxs-lookup"><span data-stu-id="771f5-115">The `Receive-PSSession` cmdlet gets the results of commands running in PowerShell sessions (**PSSession**) that were disconnected.</span></span> <span data-ttu-id="771f5-116">Om sessionen är ansluten `Receive-PSSession` hämtar resultatet från kommandon som kördes när sessionen kopplades från.</span><span class="sxs-lookup"><span data-stu-id="771f5-116">If the session is currently connected, `Receive-PSSession` gets the results of commands that were running when the session was disconnected.</span></span> <span data-ttu-id="771f5-117">Om sessionen fortfarande kopplas från `Receive-PSSession` ansluter du till sessionen, återupptar alla kommandon som har pausats och hämtar resultatet av kommandon som körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-117">If the session is still disconnected, `Receive-PSSession` connects to the session, resumes any commands that were suspended, and gets the results of commands running in the session.</span></span>

<span data-ttu-id="771f5-118">Denna cmdlet introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="771f5-118">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="771f5-119">Du kan använda en `Receive-PSSession` förutom eller i stället för ett `Connect-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="771f5-119">You can use a `Receive-PSSession` in addition to or instead of a `Connect-PSSession` command.</span></span>
<span data-ttu-id="771f5-120">`Receive-PSSession` kan ansluta till en frånkopplad eller Återansluten session som startades i andra sessioner eller på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="771f5-120">`Receive-PSSession` can connect to any disconnected or reconnected session that was started in other sessions or on other computers.</span></span>

<span data-ttu-id="771f5-121">`Receive-PSSession` fungerar på **PSSessions** som kopplades bort avsiktligt med hjälp av `Disconnect-PSSession` cmdleten eller `Invoke-Command` parametern **InDisconnectedSession** .</span><span class="sxs-lookup"><span data-stu-id="771f5-121">`Receive-PSSession` works on **PSSessions** that were disconnected intentionally using the `Disconnect-PSSession` cmdlet or the `Invoke-Command` **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="771f5-122">Eller frånkopplad oavsiktligt av ett nätverks avbrott.</span><span class="sxs-lookup"><span data-stu-id="771f5-122">Or disconnected unintentionally by a network interruption.</span></span>

<span data-ttu-id="771f5-123">Om du använder `Receive-PSSession` cmdleten för att ansluta till en session där inga kommandon körs eller pausas, `Receive-PSSession` ansluter till sessionen, men returnerar inga utdata eller fel.</span><span class="sxs-lookup"><span data-stu-id="771f5-123">If you use the `Receive-PSSession` cmdlet to connect to a session in which no commands are running or suspended, `Receive-PSSession` connects to the session, but returns no output or errors.</span></span>

<span data-ttu-id="771f5-124">Mer information om funktionen frånkopplade sessioner finns [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span><span class="sxs-lookup"><span data-stu-id="771f5-124">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="771f5-125">Några exempel använder ihopbuntning för att minska rad längden och förbättra läsbarheten.</span><span class="sxs-lookup"><span data-stu-id="771f5-125">Some examples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="771f5-126">Mer information finns i [about_Splatting](./About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="771f5-126">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="771f5-127">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="771f5-127">EXAMPLES</span></span>

### <span data-ttu-id="771f5-128">Exempel 1: Anslut till en PSSession</span><span class="sxs-lookup"><span data-stu-id="771f5-128">Example 1: Connect to a PSSession</span></span>

<span data-ttu-id="771f5-129">Det här exemplet ansluter till en session på en fjärrdator och hämtar resultatet från kommandon som körs i en session.</span><span class="sxs-lookup"><span data-stu-id="771f5-129">This example connects to a session on a remote computer and gets the results of commands that are running in a session.</span></span>

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

<span data-ttu-id="771f5-130">`Receive-PSSession`Anger den fjärranslutna datorn med parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="771f5-130">The `Receive-PSSession` specifies the remote computer with the **ComputerName** parameter.</span></span> <span data-ttu-id="771f5-131">Parametern **Name** identifierar ITTask-sessionen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="771f5-131">The **Name** parameter identifies the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="771f5-132">Exemplet hämtar resultatet från kommandon som kördes i ITTask-sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-132">The example gets the results of commands that were running in the ITTask session.</span></span>

<span data-ttu-id="771f5-133">Eftersom kommandot inte använder **mål** parametern, visas resultaten på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="771f5-133">Because the command doesn't use the **OutTarget** parameter, the results appear on the command line.</span></span>

### <span data-ttu-id="771f5-134">Exempel 2: få resultat från alla kommandon på frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="771f5-134">Example 2: Get results of all commands on disconnected sessions</span></span>

<span data-ttu-id="771f5-135">I det här exemplet hämtas resultatet av alla kommandon som körs i alla frånkopplade sessioner på två fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="771f5-135">This example gets the results of all commands running in all disconnected sessions on two remote computers.</span></span>

<span data-ttu-id="771f5-136">Om någon session inte är frånkopplad eller inte körs, `Receive-PSSession` ansluter inte till sessionen och returnerar inga utdata eller fel.</span><span class="sxs-lookup"><span data-stu-id="771f5-136">If any session wasn't disconnected or isn't running commands, `Receive-PSSession` doesn't connect to the session and doesn't return any output or errors.</span></span>

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

<span data-ttu-id="771f5-137">`Get-PSSession` använder parametern **computername** för att ange fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="771f5-137">`Get-PSSession` uses the **ComputerName** parameter to specify the remote computers.</span></span> <span data-ttu-id="771f5-138">Objekten skickas ned pipelinen till `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="771f5-138">The objects are sent down the pipeline to `Receive-PSSession`.</span></span>

### <span data-ttu-id="771f5-139">Exempel 3: Hämta resultatet av ett skript som körs i en session</span><span class="sxs-lookup"><span data-stu-id="771f5-139">Example 3: Get the results of a script running in a session</span></span>

<span data-ttu-id="771f5-140">I det här exemplet används `Receive-PSSession` cmdleten för att hämta resultatet av ett skript som kördes i en fjärrdators session.</span><span class="sxs-lookup"><span data-stu-id="771f5-140">This example uses the `Receive-PSSession` cmdlet to get the results of a script that was running in a remote computer's session.</span></span>

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

<span data-ttu-id="771f5-141">Kommandot använder parametrarna **computername** och **Name** för att identifiera den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-141">The command uses the **ComputerName** and **Name** parameters to identify the disconnected session.</span></span>
<span data-ttu-id="771f5-142">Den använder en **mål** parameter med ett värde för jobbet att dirigera `Receive-PSSession` för att returnera resultaten som ett jobb.</span><span class="sxs-lookup"><span data-stu-id="771f5-142">It uses the **OutTarget** parameter with a value of Job to direct `Receive-PSSession` to return the results as a job.</span></span> <span data-ttu-id="771f5-143">Parametern **JobName** anger ett namn för jobbet i den återanslutna sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-143">The **JobName** parameter specifies a name for the job in the reconnected session.</span></span>
<span data-ttu-id="771f5-144">Parametern **Credential** kör `Receive-PSSession` kommandot med behörigheterna för en domän administratör.</span><span class="sxs-lookup"><span data-stu-id="771f5-144">The **Credential** parameter runs the `Receive-PSSession` command using the permissions of a domain administrator.</span></span>

<span data-ttu-id="771f5-145">Utdata visar att `Receive-PSSession` de returnerade resultaten som ett jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-145">The output shows that `Receive-PSSession` returned the results as a job in the current session.</span></span> <span data-ttu-id="771f5-146">Hämta jobb resultatet med ett `Receive-Job` kommando</span><span class="sxs-lookup"><span data-stu-id="771f5-146">To get the job results, use a `Receive-Job` command</span></span>

### <span data-ttu-id="771f5-147">Exempel 4: få resultat efter ett nätverks avbrott</span><span class="sxs-lookup"><span data-stu-id="771f5-147">Example 4: Get results after a network outage</span></span>

<span data-ttu-id="771f5-148">I det här exemplet används `Receive-PSSession` cmdleten för att hämta resultatet av ett jobb när ett nätverks avbrott stör en session-anslutning.</span><span class="sxs-lookup"><span data-stu-id="771f5-148">This example uses the `Receive-PSSession` cmdlet to get the results of a job after a network outage disrupts a session connection.</span></span> <span data-ttu-id="771f5-149">PowerShell försöker automatiskt återansluta sessionen en gång per sekund under de närmaste fyra minuterna och överger bara arbets insatsen om alla försök i fyra minuter Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="771f5-149">PowerShell automatically attempts to reconnect the session once per second for the next four minutes and abandons the effort only if all attempts in the four-minute interval fail.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

<span data-ttu-id="771f5-150">`New-PSSession`Cmdleten skapar en session på Server01-datorn och sparar sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-150">The `New-PSSession` cmdlet creates a session on the Server01 computer and saves the session in the `$s` variable.</span></span> <span data-ttu-id="771f5-151">`$s`Variabeln visar att **statusen** är öppen och **att tillgängligheten** är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="771f5-151">The `$s` variable displays that the **State** is Opened and the **Availability** is Available.</span></span> <span data-ttu-id="771f5-152">Dessa värden anger att du är ansluten till sessionen och att du kan köra kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-152">These values indicate that you're connected to the session and can run commands in the session.</span></span>

<span data-ttu-id="771f5-153">`Invoke-Command`Cmdleten kör ett skript i sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-153">The `Invoke-Command` cmdlet runs a script in the session in the `$s` variable.</span></span> <span data-ttu-id="771f5-154">Skriptet börjar köra och returnera data, men ett nätverks avbrott inträffar som avbryter sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-154">The script begins to run and return data, but a network outage occurs that interrupts the session.</span></span> <span data-ttu-id="771f5-155">Användaren måste avsluta sessionen och starta om den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="771f5-155">The user has to exit the session and restart the local computer.</span></span>

<span data-ttu-id="771f5-156">När datorn startas om startar användaren PowerShell och kör ett `Get-PSSession` kommando för att hämta sessioner på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="771f5-156">When the computer restarts, the user starts PowerShell and runs a `Get-PSSession` command to get sessions on the Server01 computer.</span></span> <span data-ttu-id="771f5-157">Utdata visar att **AD** -sessionen fortfarande finns på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="771f5-157">The output shows that the **AD** session still exists on the Server01 computer.</span></span> <span data-ttu-id="771f5-158">**Statusen** anger att **AD** -sessionen är frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="771f5-158">The **State** indicates that the **AD** session is disconnected.</span></span> <span data-ttu-id="771f5-159">**Tillgänglighet** svärdet none innebär att sessionen inte är ansluten till några klientsessioner.</span><span class="sxs-lookup"><span data-stu-id="771f5-159">The **Availability** value of None, indicates that the session isn't connected to any client sessions.</span></span>

<span data-ttu-id="771f5-160">`Receive-PSSession`Cmdleten återansluter till **AD** -sessionen och hämtar resultatet från skriptet som kördes i sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-160">The `Receive-PSSession` cmdlet reconnects to the **AD** session and gets the results of the script that ran in the session.</span></span> <span data-ttu-id="771f5-161">Kommandot använder **mål** parametern för att begära resultatet i ett jobb med namnet **ADJob**.</span><span class="sxs-lookup"><span data-stu-id="771f5-161">The command uses the **OutTarget** parameter to request the results in a job named **ADJob**.</span></span> <span data-ttu-id="771f5-162">Kommandot returnerar ett jobb objekt och utdata indikerar att skriptet fortfarande körs.</span><span class="sxs-lookup"><span data-stu-id="771f5-162">The command returns a job object and the output indicates that the script is still running.</span></span>

<span data-ttu-id="771f5-163">`Get-PSSession`Cmdleten används för att kontrol lera jobb status.</span><span class="sxs-lookup"><span data-stu-id="771f5-163">The `Get-PSSession` cmdlet is used to check the job state.</span></span> <span data-ttu-id="771f5-164">Utdata bekräftar att `Receive-PSSession` cmdleten återansluter till **AD** -sessionen, som nu är öppen och tillgänglig för kommandon.</span><span class="sxs-lookup"><span data-stu-id="771f5-164">The output confirms that the `Receive-PSSession` cmdlet reconnected to the **AD** session, which is now open and available for commands.</span></span> <span data-ttu-id="771f5-165">Och skriptet återupptog körningen och hämtar skript resultatet.</span><span class="sxs-lookup"><span data-stu-id="771f5-165">And, the script resumed execution and is getting the script results.</span></span>

### <span data-ttu-id="771f5-166">Exempel 5: Återanslut till frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="771f5-166">Example 5: Reconnect to disconnected sessions</span></span>

<span data-ttu-id="771f5-167">I det här exemplet används `Receive-PSSession` cmdleten för att återansluta till sessioner som avsiktligt kopplats från och hämta resultatet av jobb som kördes i sessionerna.</span><span class="sxs-lookup"><span data-stu-id="771f5-167">This example uses the `Receive-PSSession` cmdlet to reconnect to sessions that were intentionally disconnected and get the results of jobs that were running in the sessions.</span></span>

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

<span data-ttu-id="771f5-168">`Invoke-Command`Cmdleten kör ett skript på tre fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="771f5-168">The `Invoke-Command` cmdlet runs a script on three remote computers.</span></span> <span data-ttu-id="771f5-169">Eftersom skriptet samlar in och sammanfattar data från flera databaser, tar det ofta skriptet en längre tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="771f5-169">Because the script gathers and summarizes data from multiple databases, it often takes the script an extended time to finish.</span></span> <span data-ttu-id="771f5-170">Kommandot använder parametern **InDisconnectedSession** som startar skripten och kopplar sedan omedelbart från sessionerna.</span><span class="sxs-lookup"><span data-stu-id="771f5-170">The command uses the **InDisconnectedSession** parameter that starts the scripts and then immediately disconnects the sessions.</span></span> <span data-ttu-id="771f5-171">Parametern **SessionOption** utökar **idleTimeout** -värdet för den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-171">The **SessionOption** parameter extends the **IdleTimeout** value of the disconnected session.</span></span> <span data-ttu-id="771f5-172">Frånkopplade sessioner anses vara inaktiva från det ögonblick då de är frånkopplade.</span><span class="sxs-lookup"><span data-stu-id="771f5-172">Disconnected sessions are considered idle from the moment they're disconnected.</span></span> <span data-ttu-id="771f5-173">Det är viktigt att ange tids gränsen för inaktivitet för tillräckligt länge så att kommandona kan slutföras och du kan återansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-173">It's important to set the idle time-out for long enough so that the commands can complete and you can reconnect to the session.</span></span> <span data-ttu-id="771f5-174">Du kan bara ange **idleTimeout** när du skapar **PSSession** och bara ändrar den när du kopplar från den.</span><span class="sxs-lookup"><span data-stu-id="771f5-174">You can set the **IdleTimeout** only when you create the **PSSession** and change it only when you disconnect from it.</span></span> <span data-ttu-id="771f5-175">Du kan inte ändra **idleTimeout** -värdet när du ansluter till en **PSSession** eller tar emot resultatet.</span><span class="sxs-lookup"><span data-stu-id="771f5-175">You can't change the **IdleTimeout** value when you connect to a **PSSession** or receiving its results.</span></span> <span data-ttu-id="771f5-176">När du har kört kommandot avslutar användaren PowerShell och stänger datorn.</span><span class="sxs-lookup"><span data-stu-id="771f5-176">After running the command, the user exits PowerShell and closes the computer.</span></span>

<span data-ttu-id="771f5-177">Nästa dag återupptar användaren Windows, startar PowerShell och använder `Get-PSSession` för att hämta de sessioner där skripten kördes.</span><span class="sxs-lookup"><span data-stu-id="771f5-177">The next day, the user resumes Windows, starts PowerShell, and uses `Get-PSSession` to get the sessions in which the scripts were running.</span></span> <span data-ttu-id="771f5-178">Kommandot identifierar sessionerna med dator namnet, sessionsnamnet och namnet på sessionen och sparar sessionerna i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-178">The command identifies the sessions by the computer name, session name, and the name of the session configuration and saves the sessions in the `$s` variable.</span></span> <span data-ttu-id="771f5-179">Värdet för `$s` variabeln visas och visar att sessionerna är frånkopplade, men inte är upptagna.</span><span class="sxs-lookup"><span data-stu-id="771f5-179">The value of the `$s` variable is displayed and shows that the sessions are disconnected, but aren't busy.</span></span>

<span data-ttu-id="771f5-180">`Receive-PSSession`Cmdleten ansluter till sessionerna i `$s` variabeln och hämtar resultatet.</span><span class="sxs-lookup"><span data-stu-id="771f5-180">The `Receive-PSSession` cmdlet connects to the sessions in the `$s` variable and gets their results.</span></span>
<span data-ttu-id="771f5-181">Kommandot sparar resultatet i `$Results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-181">The command saves the results in the `$Results` variable.</span></span> <span data-ttu-id="771f5-182">`$s`Variabeln visas och visar att sessionerna är anslutna och tillgängliga för kommandon.</span><span class="sxs-lookup"><span data-stu-id="771f5-182">The `$s` variable is displayed and shows that the sessions are connected and available for commands.</span></span>

<span data-ttu-id="771f5-183">Skript resultatet i `$Results` variabeln visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="771f5-183">The script results in the `$Results` variable are displayed in the PowerShell console.</span></span> <span data-ttu-id="771f5-184">Om något av resultaten är oväntat kan användaren köra kommandon i sessionerna för att undersöka rotor saken.</span><span class="sxs-lookup"><span data-stu-id="771f5-184">If any of the results are unexpected, the user can run commands in the sessions to investigate the root cause.</span></span>

### <span data-ttu-id="771f5-185">Exempel 6: köra ett jobb i en frånkopplad session</span><span class="sxs-lookup"><span data-stu-id="771f5-185">Example 6: Running a job in a disconnected session</span></span>

<span data-ttu-id="771f5-186">Det här exemplet visar vad som händer med ett jobb som körs i en frånkopplad session.</span><span class="sxs-lookup"><span data-stu-id="771f5-186">This example shows what happens to a job that's running in a disconnected session.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

<span data-ttu-id="771f5-187">`New-PSSession`Cmdleten skapar Testsessionen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="771f5-187">The `New-PSSession` cmdlet creates the Test session on the Server01 computer.</span></span> <span data-ttu-id="771f5-188">Kommandot sparar sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-188">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="771f5-189">`Invoke-Command`Cmdleten kör ett kommando i sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-189">The `Invoke-Command` cmdlet runs a command in the session in the `$s` variable.</span></span> <span data-ttu-id="771f5-190">Kommandot använder parametern **AsJob** för att köra kommandot som ett jobb och skapar jobbobjektet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-190">The command uses the **AsJob** parameter to run the command as a job and creates the job object in the current session.</span></span>
<span data-ttu-id="771f5-191">Kommandot returnerar ett jobb objekt som har sparats i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-191">The command returns a job object that's saved in the `$j` variable.</span></span> <span data-ttu-id="771f5-192">`$j`Variabeln visar jobbobjektet.</span><span class="sxs-lookup"><span data-stu-id="771f5-192">The `$j` variable displays the job object.</span></span>

<span data-ttu-id="771f5-193">Session-objektet i `$s` variabeln skickas till pipelinen till `Disconnect-PSSession` och sessionen kopplas från.</span><span class="sxs-lookup"><span data-stu-id="771f5-193">The session object in the `$s` variable is sent down the pipeline to `Disconnect-PSSession` and the session is disconnected.</span></span>

<span data-ttu-id="771f5-194">`$j`Variabeln visas och visar effekterna av att koppla bort jobbobjektet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-194">The `$j` variable is displayed and shows the effect of disconnecting the job object in the `$j` variable.</span></span> <span data-ttu-id="771f5-195">Jobbets tillstånd är nu frånkopplat.</span><span class="sxs-lookup"><span data-stu-id="771f5-195">The job state is now Disconnected.</span></span>

<span data-ttu-id="771f5-196">`Receive-Job`Körs på jobbet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-196">The `Receive-Job` is run on the job in the `$j` variable.</span></span> <span data-ttu-id="771f5-197">Utdata visar att jobbet började returnera utdata innan sessionen och jobbet kopplades från.</span><span class="sxs-lookup"><span data-stu-id="771f5-197">The output shows that the job began to return output before the session and the job were disconnected.</span></span>

<span data-ttu-id="771f5-198">`Connect-PSSession`Cmdleten körs i samma klient-session.</span><span class="sxs-lookup"><span data-stu-id="771f5-198">The `Connect-PSSession` cmdlet is run in the same client session.</span></span> <span data-ttu-id="771f5-199">Kommandot återansluter till Testsessionen på Server01-datorn och sparar sessionen i `$s2` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-199">The command reconnects to the Test session on the Server01 computer and saves the session in the `$s2` variable.</span></span>

<span data-ttu-id="771f5-200">`Receive-PSSession`Cmdlet: en hämtar resultatet av jobbet som kördes i sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-200">The `Receive-PSSession` cmdlet gets the results of the job that was running in the session.</span></span> <span data-ttu-id="771f5-201">Eftersom kommandot körs i samma session `Receive-PSSession` returnerar resultatet som ett jobb som standard och återanvänder samma jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="771f5-201">Because the command is run in the same session, `Receive-PSSession` returns the results as a job by default and reuses the same job object.</span></span> <span data-ttu-id="771f5-202">Kommandot sparar jobbet i `$j2` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-202">The command saves the job in the `$j2` variable.</span></span> <span data-ttu-id="771f5-203">`Receive-Job`Cmdlet: en hämtar resultatet av jobbet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-203">The `Receive-Job` cmdlet gets the results of the job in the `$j` variable.</span></span>

## <span data-ttu-id="771f5-204">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="771f5-204">PARAMETERS</span></span>

### <span data-ttu-id="771f5-205">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="771f5-205">-AllowRedirection</span></span>

<span data-ttu-id="771f5-206">Anger att denna cmdlet tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="771f5-206">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="771f5-207">När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI.</span><span class="sxs-lookup"><span data-stu-id="771f5-207">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="771f5-208">Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern för att aktivera den för att omdirigera anslutningen.</span><span class="sxs-lookup"><span data-stu-id="771f5-208">By default, PowerShell doesn't redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="771f5-209">Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session.</span><span class="sxs-lookup"><span data-stu-id="771f5-209">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="771f5-210">Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för `$PSSessionOption` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="771f5-210">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="771f5-211">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="771f5-211">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-212">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="771f5-212">-ApplicationName</span></span>

<span data-ttu-id="771f5-213">Anger ett program.</span><span class="sxs-lookup"><span data-stu-id="771f5-213">Specifies an application.</span></span> <span data-ttu-id="771f5-214">Denna cmdlet ansluter bara till sessioner som använder det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="771f5-214">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="771f5-215">Ange program namns segmentet för anslutnings-URI: n.</span><span class="sxs-lookup"><span data-stu-id="771f5-215">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="771f5-216">Till exempel är WSMan i följande anslutnings-URI program namnet: `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="771f5-216">For example, in the following connection URI, WSMan is the application name: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="771f5-217">Program namnet för en session lagras i egenskapen **körnings utrymme. ConnectionInfo. APPNAME** för sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-217">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="771f5-218">Parameterns värde används för att välja och filtrera sessioner.</span><span class="sxs-lookup"><span data-stu-id="771f5-218">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="771f5-219">Den ändrar inte det program som används av sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-219">It doesn't change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-220">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="771f5-220">-Authentication</span></span>

<span data-ttu-id="771f5-221">Anger mekanismen som används för att autentisera användarautentiseringsuppgifter i kommandot för att återansluta till en frånkopplad session.</span><span class="sxs-lookup"><span data-stu-id="771f5-221">Specifies the mechanism that's used to authenticate the user credentials in the command to reconnect to a disconnected session.</span></span> <span data-ttu-id="771f5-222">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="771f5-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="771f5-223">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="771f5-223">Default</span></span>
- <span data-ttu-id="771f5-224">Grundläggande</span><span class="sxs-lookup"><span data-stu-id="771f5-224">Basic</span></span>
- <span data-ttu-id="771f5-225">CredSSP</span><span class="sxs-lookup"><span data-stu-id="771f5-225">Credssp</span></span>
- <span data-ttu-id="771f5-226">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="771f5-226">Digest</span></span>
- <span data-ttu-id="771f5-227">Kerberos</span><span class="sxs-lookup"><span data-stu-id="771f5-227">Kerberos</span></span>
- <span data-ttu-id="771f5-228">Negotiate</span><span class="sxs-lookup"><span data-stu-id="771f5-228">Negotiate</span></span>
- <span data-ttu-id="771f5-229">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="771f5-229">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="771f5-230">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="771f5-230">The default value is Default.</span></span>

<span data-ttu-id="771f5-231">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="771f5-231">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="771f5-232">CredSSP-autentisering (Credential Security Support Provider), där användarautentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="771f5-232">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="771f5-233">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="771f5-233">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="771f5-234">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-234">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-235">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="771f5-235">-CertificateThumbprint</span></span>

<span data-ttu-id="771f5-236">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att ansluta till den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-236">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="771f5-237">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="771f5-237">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="771f5-238">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="771f5-238">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="771f5-239">Certifikat kan endast mappas till lokala användar konton och fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="771f5-239">Certificates can be mapped only to local user accounts, and don't work with domain accounts.</span></span>

<span data-ttu-id="771f5-240">Om du vill hämta ett tumavtryck för certifikatet använder du ett `Get-Item` eller- `Get-ChildItem` kommando i PowerShell- `Cert:` enheten.</span><span class="sxs-lookup"><span data-stu-id="771f5-240">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-241">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="771f5-241">-ComputerName</span></span>

<span data-ttu-id="771f5-242">Anger den dator där den frånkopplade sessionen lagras.</span><span class="sxs-lookup"><span data-stu-id="771f5-242">Specifies the computer on which the disconnected session is stored.</span></span> <span data-ttu-id="771f5-243">Sessioner lagras på den dator som finns på Server sidan eller tar emot en anslutning till slutet.</span><span class="sxs-lookup"><span data-stu-id="771f5-243">Sessions are stored on the computer that's at the server-side, or receiving end of a connection.</span></span> <span data-ttu-id="771f5-244">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="771f5-244">The default is the local computer.</span></span>

<span data-ttu-id="771f5-245">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en dator.</span><span class="sxs-lookup"><span data-stu-id="771f5-245">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of one computer.</span></span>
<span data-ttu-id="771f5-246">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="771f5-246">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="771f5-247">Om du vill ange den lokala datorn skriver du datorns namn, en punkt ( `.` ), `$env:COMPUTERNAME` eller localhost.</span><span class="sxs-lookup"><span data-stu-id="771f5-247">To specify the local computer, type the computer name, a dot (`.`), `$env:COMPUTERNAME`, or localhost.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-248">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="771f5-248">-ConfigurationName</span></span>

<span data-ttu-id="771f5-249">Anger namnet på en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-249">Specifies the name of a session configuration.</span></span> <span data-ttu-id="771f5-250">Denna cmdlet ansluter bara till sessioner som använder den angivna sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-250">This cmdlet connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="771f5-251">Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-251">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="771f5-252">Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix:</span><span class="sxs-lookup"><span data-stu-id="771f5-252">If you specify only the configuration name, the following schema URI is prepended:</span></span>

<span data-ttu-id="771f5-253">`http://schemas.microsoft.com/powershell`.</span><span class="sxs-lookup"><span data-stu-id="771f5-253">`http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="771f5-254">Konfigurations namnet för en session lagras i sessionens **ConfigurationName** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="771f5-254">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="771f5-255">Parameterns värde används för att välja och filtrera sessioner.</span><span class="sxs-lookup"><span data-stu-id="771f5-255">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="771f5-256">Den ändrar inte den sessionsinformation som sessionen använder.</span><span class="sxs-lookup"><span data-stu-id="771f5-256">It doesn't change the session configuration that the session uses.</span></span>

<span data-ttu-id="771f5-257">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](./About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="771f5-257">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-258">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="771f5-258">-ConnectionUri</span></span>

<span data-ttu-id="771f5-259">Anger en URI som definierar den anslutnings slut punkt som används för att återansluta till den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-259">Specifies a URI that defines the connection endpoint that is used to reconnect to the disconnected session.</span></span>

<span data-ttu-id="771f5-260">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="771f5-260">The URI must be fully qualified.</span></span> <span data-ttu-id="771f5-261">Strängens format är följande:</span><span class="sxs-lookup"><span data-stu-id="771f5-261">The string's format is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="771f5-262">Standardvärdet är följande:</span><span class="sxs-lookup"><span data-stu-id="771f5-262">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="771f5-263">Om du inte anger en anslutnings-URI kan du använda parametrarna **UseSSL**, **computername**, **port** och **ApplicationName** för att ange anslutnings-URI-värden.</span><span class="sxs-lookup"><span data-stu-id="771f5-263">If you don't specify a connection URI, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="771f5-264">Giltiga värden för URI: n i **transport** segmentet är http och https.</span><span class="sxs-lookup"><span data-stu-id="771f5-264">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="771f5-265">Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="771f5-265">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with standard ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="771f5-266">Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="771f5-266">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="771f5-267">Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="771f5-267">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-268">-Credential</span><span class="sxs-lookup"><span data-stu-id="771f5-268">-Credential</span></span>

<span data-ttu-id="771f5-269">Anger ett användar konto som har behörighet att ansluta till den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-269">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="771f5-270">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="771f5-270">The default is the current user.</span></span>

<span data-ttu-id="771f5-271">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="771f5-271">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="771f5-272">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="771f5-272">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="771f5-273">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="771f5-273">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="771f5-274">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="771f5-274">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-275">-ID</span><span class="sxs-lookup"><span data-stu-id="771f5-275">-Id</span></span>

<span data-ttu-id="771f5-276">Anger ID för en frånkopplad session.</span><span class="sxs-lookup"><span data-stu-id="771f5-276">Specifies the ID of a disconnected session.</span></span> <span data-ttu-id="771f5-277">**ID-** parametern fungerar bara när den frånkopplade sessionen tidigare var ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-277">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="771f5-278">Den här parametern är giltig, men inte effektiv, när sessionen lagras på den lokala datorn, men inte var ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-278">This parameter is valid, but not effective, when the session is stored on the local computer, but wasn't connected to the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-279">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="771f5-279">-InstanceId</span></span>

<span data-ttu-id="771f5-280">Anger instans-ID för den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-280">Specifies the instance ID of the disconnected session.</span></span> <span data-ttu-id="771f5-281">Instans-ID är ett GUID som unikt identifierar en **PSSession** på en lokal eller fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="771f5-281">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span> <span data-ttu-id="771f5-282">Instans-ID: t lagras i egenskapen **InstanceID** i **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="771f5-282">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-283">– JobName</span><span class="sxs-lookup"><span data-stu-id="771f5-283">-JobName</span></span>

<span data-ttu-id="771f5-284">Anger ett eget namn för jobbet som `Receive-PSSession` returneras.</span><span class="sxs-lookup"><span data-stu-id="771f5-284">Specifies a friendly name for the job that `Receive-PSSession` returns.</span></span>

<span data-ttu-id="771f5-285">`Receive-PSSession` Returnerar ett jobb när värdet för **mål** parametern är Job eller jobbet som körs i den frånkopplade sessionen startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-285">`Receive-PSSession` returns a job when the value of the **OutTarget** parameter is Job or the job that's running in the disconnected session was started in the current session.</span></span>

<span data-ttu-id="771f5-286">Om jobbet som körs i den frånkopplade sessionen startades i den aktuella sessionen återanvänder PowerShell det ursprungliga jobbobjektet i sessionen och ignorerar värdet för parametern **JobName** .</span><span class="sxs-lookup"><span data-stu-id="771f5-286">If the job that's running in the disconnected session was started in the current session, PowerShell reuses the original job object in the session and ignores the value of the **JobName** parameter.</span></span>

<span data-ttu-id="771f5-287">Om jobbet som körs i den frånkopplade sessionen startades i en annan session, skapar PowerShell ett nytt jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="771f5-287">If the job that's running in the disconnected session was started in a different session, PowerShell creates a new job object.</span></span> <span data-ttu-id="771f5-288">Ett standard namn används, men du kan använda den här parametern för att ändra namnet.</span><span class="sxs-lookup"><span data-stu-id="771f5-288">It uses a default name, but you can use this parameter to change the name.</span></span>

<span data-ttu-id="771f5-289">Om standardvärdet eller det explicita värdet för **mål** parametern inte är jobb, lyckas kommandot, men parametern **JobName** har ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="771f5-289">If the default value or explicit value of the **OutTarget** parameter isn't Job, the command succeeds, but the **JobName** parameter has no effect.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-290">-Name</span><span class="sxs-lookup"><span data-stu-id="771f5-290">-Name</span></span>

<span data-ttu-id="771f5-291">Anger det egna namnet på den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-291">Specifies the friendly name of the disconnected session.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-292">-Mål</span><span class="sxs-lookup"><span data-stu-id="771f5-292">-OutTarget</span></span>

<span data-ttu-id="771f5-293">Anger hur sessionens resultat returneras.</span><span class="sxs-lookup"><span data-stu-id="771f5-293">Determines how the session results are returned.</span></span> <span data-ttu-id="771f5-294">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="771f5-294">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="771f5-295">**Jobb**.</span><span class="sxs-lookup"><span data-stu-id="771f5-295">**Job**.</span></span> <span data-ttu-id="771f5-296">Returnerar resultatet asynkront i ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="771f5-296">Returns the results asynchronously in a job object.</span></span> <span data-ttu-id="771f5-297">Du kan använda parametern **JobName** för att ange ett namn eller ett nytt namn för jobbet.</span><span class="sxs-lookup"><span data-stu-id="771f5-297">You can use the **JobName** parameter to specify a name or new name for the job.</span></span>
- <span data-ttu-id="771f5-298">**Värd**.</span><span class="sxs-lookup"><span data-stu-id="771f5-298">**Host**.</span></span> <span data-ttu-id="771f5-299">Returnerar resultaten till kommando raden (synkront).</span><span class="sxs-lookup"><span data-stu-id="771f5-299">Returns the results to the command line (synchronously).</span></span> <span data-ttu-id="771f5-300">Om kommandot återupptas eller om resultatet består av ett stort antal objekt, kan svaret vara försenat.</span><span class="sxs-lookup"><span data-stu-id="771f5-300">If the command is being resumed or the results consist of a large number of objects, the response might be delayed.</span></span>

<span data-ttu-id="771f5-301">Standardvärdet för **mål** parametern är Host.</span><span class="sxs-lookup"><span data-stu-id="771f5-301">The default value of the **OutTarget** parameter is Host.</span></span> <span data-ttu-id="771f5-302">Om kommandot som tas emot i en frånkopplad session startades i den aktuella sessionen, är standardvärdet för **mål** parametern det formulär där kommandot startades.</span><span class="sxs-lookup"><span data-stu-id="771f5-302">If the command that's being received in a disconnected session was started in the current session, the default value of the **OutTarget** parameter is the form in which the command was started.</span></span> <span data-ttu-id="771f5-303">Om kommandot startades som ett jobb returneras det som standard som ett jobb.</span><span class="sxs-lookup"><span data-stu-id="771f5-303">If the command was started as a job, by default, it's returned as a job.</span></span> <span data-ttu-id="771f5-304">Annars returneras de till värd programmet som standard.</span><span class="sxs-lookup"><span data-stu-id="771f5-304">Otherwise, it's returned to the host program by default.</span></span>

<span data-ttu-id="771f5-305">Normalt visar värd programmet returnerade objekt på kommando raden utan fördröjning, men det här beteendet kan variera.</span><span class="sxs-lookup"><span data-stu-id="771f5-305">Typically, the host program displays returned objects at the command line without delay, but this behavior can vary.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-306">-Port</span><span class="sxs-lookup"><span data-stu-id="771f5-306">-Port</span></span>

<span data-ttu-id="771f5-307">Anger fjärrdatorns nätverks port som används för att återansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-307">Specifies the remote computer's network port that's used to reconnect to the session.</span></span> <span data-ttu-id="771f5-308">Om du vill ansluta till en fjärrdator måste den lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="771f5-308">To connect to a remote computer, it must be listening on the port that the connection uses.</span></span> <span data-ttu-id="771f5-309">Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="771f5-309">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="771f5-310">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="771f5-310">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen on that port.</span></span> <span data-ttu-id="771f5-311">Konfigurera lyssnaren genom att skriva följande två kommandon i PowerShell-prompten:</span><span class="sxs-lookup"><span data-stu-id="771f5-311">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="771f5-312">Använd inte **port** parametern om det inte behövs.</span><span class="sxs-lookup"><span data-stu-id="771f5-312">Don't use the **Port** parameter unless it's necessary.</span></span> <span data-ttu-id="771f5-313">Porten som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="771f5-313">The port that's set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="771f5-314">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="771f5-314">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-315">– Session</span><span class="sxs-lookup"><span data-stu-id="771f5-315">-Session</span></span>

<span data-ttu-id="771f5-316">Anger den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-316">Specifies the disconnected session.</span></span> <span data-ttu-id="771f5-317">Ange en variabel som innehåller **PSSession** eller ett kommando som skapar eller hämtar **PSSession**, till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="771f5-317">Enter a variable that contains the **PSSession** or a command that creates or gets the **PSSession**, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-318">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="771f5-318">-SessionOption</span></span>

<span data-ttu-id="771f5-319">Anger avancerade alternativ för sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-319">Specifies advanced options for the session.</span></span> <span data-ttu-id="771f5-320">Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.</span><span class="sxs-lookup"><span data-stu-id="771f5-320">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="771f5-321">Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="771f5-321">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="771f5-322">Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-322">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="771f5-323">Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-323">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="771f5-324">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-324">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="771f5-325">En beskrivning av de sessionsinformation som innehåller standardvärdena finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="771f5-325">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="771f5-326">Information om variabeln **$PSSessionOption** finns i [about_Preference_Variables](./About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="771f5-326">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span> <span data-ttu-id="771f5-327">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](./About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="771f5-327">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-328">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="771f5-328">-UseSSL</span></span>

<span data-ttu-id="771f5-329">Anger att denna cmdlet använder Secure Sockets Layer (SSL)-protokollet för att ansluta till den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-329">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="771f5-330">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="771f5-330">By default, SSL isn't used.</span></span>

<span data-ttu-id="771f5-331">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="771f5-331">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="771f5-332">**UseSSL** är ett ytterligare skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="771f5-332">**UseSSL** is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="771f5-333">Om du använder den här parametern och SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="771f5-333">If you use this parameter and SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="771f5-334">-Confirm</span><span class="sxs-lookup"><span data-stu-id="771f5-334">-Confirm</span></span>

<span data-ttu-id="771f5-335">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="771f5-335">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="771f5-336">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="771f5-336">-WhatIf</span></span>

<span data-ttu-id="771f5-337">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="771f5-337">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="771f5-338">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="771f5-338">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="771f5-339">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="771f5-339">CommonParameters</span></span>

<span data-ttu-id="771f5-340">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="771f5-340">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="771f5-341">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="771f5-341">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="771f5-342">INDATA</span><span class="sxs-lookup"><span data-stu-id="771f5-342">INPUTS</span></span>

### <span data-ttu-id="771f5-343">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="771f5-343">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="771f5-344">Du kan skicka pipe-sessionsobjekt till denna cmdlet, till exempel objekt som returneras av `Get-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="771f5-344">You can pipe session objects to this cmdlet, such as objects returned by the `Get-PSSession` cmdlet.</span></span>

### <span data-ttu-id="771f5-345">System. Int32</span><span class="sxs-lookup"><span data-stu-id="771f5-345">System.Int32</span></span>

<span data-ttu-id="771f5-346">Du kan skicka pipe-sessions-ID: n till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="771f5-346">You can pipe session Ids to this cmdlet.</span></span>

### <span data-ttu-id="771f5-347">System. GUID</span><span class="sxs-lookup"><span data-stu-id="771f5-347">System.Guid</span></span>

<span data-ttu-id="771f5-348">Du kan skicka vidare instans-ID för sessioner denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="771f5-348">You can pipe the instance Ids of sessions this cmdlet.</span></span>

### <span data-ttu-id="771f5-349">System. String</span><span class="sxs-lookup"><span data-stu-id="771f5-349">System.String</span></span>

<span data-ttu-id="771f5-350">Du kan skicka pipe-sessionsnamn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="771f5-350">You can pipe session names to this cmdlet.</span></span>

## <span data-ttu-id="771f5-351">UTDATA</span><span class="sxs-lookup"><span data-stu-id="771f5-351">OUTPUTS</span></span>

### <span data-ttu-id="771f5-352">System. Management. Automation. job eller PSObject</span><span class="sxs-lookup"><span data-stu-id="771f5-352">System.Management.Automation.Job or PSObject</span></span>

<span data-ttu-id="771f5-353">Den här cmdleten returnerar resultatet av kommandon som kördes i den frånkopplade sessionen, om det finns några.</span><span class="sxs-lookup"><span data-stu-id="771f5-353">This cmdlet returns the results of commands that ran in the disconnected session, if any.</span></span> <span data-ttu-id="771f5-354">Om värdet eller standardvärdet för **mål** parametern är Job, `Receive-PSSession` returnerar ett Job-objekt.</span><span class="sxs-lookup"><span data-stu-id="771f5-354">If the value or default value of the **OutTarget** parameter is Job, `Receive-PSSession` returns a job object.</span></span> <span data-ttu-id="771f5-355">Annars returneras objekt som representerar kommando resultatet.</span><span class="sxs-lookup"><span data-stu-id="771f5-355">Otherwise, it returns objects that represent that command results.</span></span>

## <span data-ttu-id="771f5-356">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="771f5-356">NOTES</span></span>

<span data-ttu-id="771f5-357">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="771f5-357">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="771f5-358">`Receive-PSSession` hämtar endast resultat från sessioner som kopplats från.</span><span class="sxs-lookup"><span data-stu-id="771f5-358">`Receive-PSSession` gets results only from sessions that were disconnected.</span></span> <span data-ttu-id="771f5-359">Endast sessioner som är anslutna till eller avslutas på datorer som kör PowerShell 3,0 eller senare versioner kan kopplas från och återanslutas.</span><span class="sxs-lookup"><span data-stu-id="771f5-359">Only sessions that are connected to, or terminate at, computers that run PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

<span data-ttu-id="771f5-360">Om kommandona som kördes i den frånkopplade sessionen inte genererade resultat eller om resultatet redan returnerades till en annan session, `Receive-PSSession` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="771f5-360">If the commands that were running in the disconnected session didn't generate results or if the results were already returned to another session, `Receive-PSSession` doesn't generate any output.</span></span>

<span data-ttu-id="771f5-361">En sessions buffer buffer-läge avgör hur kommandon i sessionen hanterar utdata när sessionen kopplas från.</span><span class="sxs-lookup"><span data-stu-id="771f5-361">A session's output buffering mode determines how commands in the session manage output when the session is disconnected.</span></span> <span data-ttu-id="771f5-362">När värdet för **OutputBufferingMode** -alternativet för sessionen släpps och utdatabufferten är full börjar kommandot Ta bort utdata.</span><span class="sxs-lookup"><span data-stu-id="771f5-362">When the value of the **OutputBufferingMode** option of the session is Drop and the output buffer is full, the command starts to delete output.</span></span> <span data-ttu-id="771f5-363">`Receive-PSSession` Det går inte att återställa utdata.</span><span class="sxs-lookup"><span data-stu-id="771f5-363">`Receive-PSSession` can't recover this output.</span></span> <span data-ttu-id="771f5-364">Mer information om alternativet utdata buffation mode finns i hjälp artiklarna för cmdletarna [New-PSSessionOption](New-PSSessionOption.md) och [New-PSTransportOption](New-PSTransportOption.md) .</span><span class="sxs-lookup"><span data-stu-id="771f5-364">For more information about the output buffering mode option, see the help articles for the [New-PSSessionOption](New-PSSessionOption.md) and [New-PSTransportOption](New-PSTransportOption.md) cmdlets.</span></span>

<span data-ttu-id="771f5-365">Du kan inte ändra timeout-värdet för inaktivitet för en **PSSession** när du ansluter till **PSSession** eller ta emot resultat.</span><span class="sxs-lookup"><span data-stu-id="771f5-365">You can't change the idle time-out value of a **PSSession** when you connect to the **PSSession** or receive results.</span></span> <span data-ttu-id="771f5-366">Parametern **SessionOption** för `Receive-PSSession` använder ett **SessionOption** -objekt som har ett **idleTimeout** -värde.</span><span class="sxs-lookup"><span data-stu-id="771f5-366">The **SessionOption** parameter of `Receive-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="771f5-367">Men **idleTimeout** -värdet för objektet **SessionOption** och **idleTimeout** -värdet för `$PSSessionOption` variabeln ignoreras när det ansluter till en **PSSession** eller tar emot resultat.</span><span class="sxs-lookup"><span data-stu-id="771f5-367">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when it connects to a **PSSession** or receiving results.</span></span>

- <span data-ttu-id="771f5-368">Du kan ange och ändra tids gränsen för inaktivitet i en **PSSession** när du skapar **PSSession**, genom att använda `New-PSSession` `Invoke-Command` cmdletarna eller och när du kopplar bort från **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="771f5-368">You can set and change the idle time-out of a **PSSession** when you create the **PSSession**, by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>
- <span data-ttu-id="771f5-369">Egenskapen **idleTimeout** för en **PSSession** är kritisk för frånkopplade sessioner eftersom den fastställer hur länge en frånkopplad session ska bevaras på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="771f5-369">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="771f5-370">Frånkopplade sessioner anses vara inaktiva från det ögonblick då de kopplas från, även om kommandon körs i den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-370">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="771f5-371">Om du startar ett jobb i en fjärrsession med hjälp av parametern **AsJob** i `Invoke-Command` cmdleten, skapas jobbobjektet i den aktuella sessionen, även om jobbet körs i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-371">If you start a start a job in a remote session by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is created in the current session, even though the job runs in the remote session.</span></span> <span data-ttu-id="771f5-372">Om du kopplar från fjärrsessionen kopplas jobbobjektet i den aktuella sessionen bort från jobbet.</span><span class="sxs-lookup"><span data-stu-id="771f5-372">If you disconnect the remote session, the job object in the current session is disconnected from the job.</span></span> <span data-ttu-id="771f5-373">Jobbobjektet innehåller alla resultat som returnerades till det, men som inte får nya resultat från jobbet i den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-373">The job object contains any results that were returned to it, but doesn't receive new results from the job in the disconnected session.</span></span>

<span data-ttu-id="771f5-374">Om en annan klient ansluter till sessionen som innehåller det jobb som körs är de resultat som levererades till det ursprungliga jobbobjektet i den ursprungliga sessionen inte tillgängliga i den nyligen anslutna sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-374">If a different client connects to the session that contains the running job, the results that were delivered to the original job object in the original session aren't available in the newly connected session.</span></span> <span data-ttu-id="771f5-375">Endast resultat som inte levererades till det ursprungliga jobbobjektet är tillgängliga i den återanslutna sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-375">Only results that were not delivered to the original job object are available in the reconnected session.</span></span>

<span data-ttu-id="771f5-376">På samma sätt, om du startar ett skript i en session och sedan kopplar bort från sessionen, kommer alla resultat som skriptet levererar till sessionen innan från koppling inte är tillgängliga för en annan klient som ansluter till sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-376">Similarly, if you start a script in a session and then disconnect from the session, any results that the script delivers to the session before disconnecting aren't available to another client that connects to the session.</span></span>

<span data-ttu-id="771f5-377">Använd parametern **InDisconnectedSession** för cmdleten för att förhindra data förlust i sessioner som du vill koppla från `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="771f5-377">To prevent data loss in sessions that you intend to disconnect, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="771f5-378">Eftersom den här parametern förhindrar att resultat returneras till den aktuella sessionen, är alla resultat tillgängliga när sessionen återansluts.</span><span class="sxs-lookup"><span data-stu-id="771f5-378">Because this parameter prevents results from being returned to the current session, all results are available when the session is reconnected.</span></span>

<span data-ttu-id="771f5-379">Du kan även förhindra data förlust genom att använda `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-379">You can also prevent data loss by using the `Invoke-Command` cmdlet to run a `Start-Job` command in the remote session.</span></span> <span data-ttu-id="771f5-380">I det här fallet skapas jobbobjektet i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-380">In this case, the job object is created in the remote session.</span></span> <span data-ttu-id="771f5-381">Du kan inte använda `Receive-PSSession` cmdlet: en för att hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="771f5-381">You can't use the `Receive-PSSession` cmdlet to get the job results.</span></span> <span data-ttu-id="771f5-382">Använd i stället cmdlet: en `Connect-PSSession` för att ansluta till sessionen och Använd sedan `Invoke-Command` cmdleten för att köra ett `Receive-Job` kommando i sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-382">Instead, use the `Connect-PSSession` cmdlet to connect to the session and then use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session.</span></span>

<span data-ttu-id="771f5-383">När en session som innehåller ett jobb som körs är frånkopplad och sedan ansluts igen återanvänds det ursprungliga jobbobjektet endast om jobbet är frånkopplat och återanslutits till samma session, och kommandot för att återansluta inte anger ett nytt jobbnamn.</span><span class="sxs-lookup"><span data-stu-id="771f5-383">When a session that contains a running job is disconnected and then reconnected, the original job object is reused only if the job is disconnected and reconnected to the same session, and the command to reconnect doesn't specify a new job name.</span></span> <span data-ttu-id="771f5-384">Om sessionen återansluts till en annan klientsession eller om ett nytt jobbnamn anges, skapar PowerShell ett nytt jobb objekt för den nya sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-384">If the session is reconnected to a different client session or a new job name is specified, PowerShell creates a new job object for the new session.</span></span>

<span data-ttu-id="771f5-385">När du kopplar från en **PSSession** kopplas sessionstillståndet ned och tillgängligheten är ingen.</span><span class="sxs-lookup"><span data-stu-id="771f5-385">When you disconnect a **PSSession**, the session state is Disconnected and the availability is None.</span></span>

- <span data-ttu-id="771f5-386">Värdet för egenskapen **State** är i förhållande till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-386">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="771f5-387">Värdet frånkopplat innebär att **PSSession** inte är ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-387">A value of Disconnected means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="771f5-388">Det innebär dock inte att **PSSession** är frånkopplad från alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="771f5-388">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="771f5-389">Den kan vara ansluten till en annan session.</span><span class="sxs-lookup"><span data-stu-id="771f5-389">It might be connected to a different session.</span></span>
  <span data-ttu-id="771f5-390">Använd egenskapen **tillgänglighet** för att avgöra om du kan ansluta eller återansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-390">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>
- <span data-ttu-id="771f5-391">**Tillgänglighet** svärdet none anger att du kan ansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="771f5-391">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="771f5-392">Värdet upptagen anger att du inte kan ansluta till **PSSession** eftersom det är anslutet till en annan session.</span><span class="sxs-lookup"><span data-stu-id="771f5-392">A value of Busy indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span>
- <span data-ttu-id="771f5-393">Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="771f5-393">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>
- <span data-ttu-id="771f5-394">Mer information om värdena för egenskapen **Availability** för sessioner finns i [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="771f5-394">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="771f5-395">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="771f5-395">RELATED LINKS</span></span>

[<span data-ttu-id="771f5-396">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="771f5-396">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="771f5-397">about_Remote</span><span class="sxs-lookup"><span data-stu-id="771f5-397">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="771f5-398">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="771f5-398">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="771f5-399">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="771f5-399">about_Session_Configurations</span></span>](./About/about_Session_Configurations.md)

[<span data-ttu-id="771f5-400">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="771f5-400">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="771f5-401">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="771f5-401">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="771f5-402">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="771f5-402">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="771f5-403">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="771f5-403">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="771f5-404">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="771f5-404">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="771f5-405">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="771f5-405">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="771f5-406">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="771f5-406">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="771f5-407">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="771f5-407">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="771f5-408">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="771f5-408">Remove-PSSession</span></span>](Remove-PSSession.md)