---
description: Förklarar hur du kopplar från och återansluter till en PowerShell-session (PSSession).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 2f352ab123618f1ab9617e9d300f10f7a5e5928a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270483"
---
# <a name="about-remote-disconnected-sessions"></a><span data-ttu-id="5e851-104">Om fjärranslutna sessioner</span><span class="sxs-lookup"><span data-stu-id="5e851-104">About Remote Disconnected Sessions</span></span>

## <a name="short-description"></a><span data-ttu-id="5e851-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="5e851-105">Short description</span></span>

<span data-ttu-id="5e851-106">Förklarar hur du kopplar från och återansluter till en PowerShell-session (PSSession).</span><span class="sxs-lookup"><span data-stu-id="5e851-106">Explains how to disconnect and reconnect to a PowerShell Session (PSSession).</span></span>

## <a name="long-description"></a><span data-ttu-id="5e851-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="5e851-107">Long description</span></span>

<span data-ttu-id="5e851-108">Från och med PowerShell 3,0 kan du koppla från en PSSession och återansluta till PSSession på samma dator eller en annan dator.</span><span class="sxs-lookup"><span data-stu-id="5e851-108">Beginning in PowerShell 3.0, you can disconnect from a PSSession and reconnect to the PSSession on the same computer or a different computer.</span></span> <span data-ttu-id="5e851-109">Sessionstillståndet upprätthålls och kommandon i PSSession fortsätter att köras medan sessionen kopplas från.</span><span class="sxs-lookup"><span data-stu-id="5e851-109">The session state is maintained and commands in the PSSession continue to run while the session is disconnected.</span></span>

<span data-ttu-id="5e851-110">Funktionen frånkopplade sessioner är bara tillgänglig när fjärrdatorn kör PowerShell 3,0 eller en senare version.</span><span class="sxs-lookup"><span data-stu-id="5e851-110">The Disconnected Sessions feature is only available when the remote computer is running PowerShell 3.0 or a later version.</span></span>

<span data-ttu-id="5e851-111">Med funktionen frånkopplade sessioner kan du stänga sessionen där en PSSession skapades, och till och med stänga PowerShell och stänga av datorn, utan att avbryta kommandon som körs i PSSession.</span><span class="sxs-lookup"><span data-stu-id="5e851-111">The Disconnected Sessions feature allows you to close the session in which a PSSession was created, and even close PowerShell, and shut down the computer, without disrupting commands running in the PSSession.</span></span> <span data-ttu-id="5e851-112">Frånkopplade sessioner är användbara för att köra kommandon som tar lång tid att slutföra och ger den tid och den flexibilitet som IT-proffs kräver.</span><span class="sxs-lookup"><span data-stu-id="5e851-112">Disconnected sessions are useful for running commands that take an extended time to complete, and provides the time and device flexibility that IT professionals require.</span></span>

<span data-ttu-id="5e851-113">Du kan inte koppla från en interaktiv session som har startats med hjälp av `Enter-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e851-113">You can't disconnect from an interactive session that is started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="5e851-114">Du kan använda frånkopplade sessioner för att hantera PSSessions som frånkopplats oavsiktligt på grund av en dators eller ett nätverks avbrott.</span><span class="sxs-lookup"><span data-stu-id="5e851-114">You can use disconnected sessions to manage PSSessions that were disconnected unintentionally as the result of a computer or network outage.</span></span>

<span data-ttu-id="5e851-115">I verkligheten kan du använda funktionen frånkopplade sessioner för att lösa ett problem, förvandla din uppmärksamhet till ett problem med högre prioritet och sedan återuppta arbetet med lösningen, även på en annan dator på en annan plats.</span><span class="sxs-lookup"><span data-stu-id="5e851-115">In real-world use, the Disconnected Sessions feature allows you to begin solving a problem, turn your attention to a higher priority issue, and then resume work on the solution, even on a different computer in a different location.</span></span>

## <a name="disconnected-session-cmdlets"></a><span data-ttu-id="5e851-116">Cmdletar för frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="5e851-116">Disconnected session cmdlets</span></span>

<span data-ttu-id="5e851-117">Följande cmdletar stöder funktionen frånkopplade sessioner:</span><span class="sxs-lookup"><span data-stu-id="5e851-117">The following cmdlets support the Disconnected Sessions feature:</span></span>

- <span data-ttu-id="5e851-118">`Connect-PSSession`: Ansluter till en frånkopplad PSSession.</span><span class="sxs-lookup"><span data-stu-id="5e851-118">`Connect-PSSession`: Connects to a disconnected PSSession.</span></span>
- <span data-ttu-id="5e851-119">`Disconnect-PSSession`: Kopplar från en PSSession.</span><span class="sxs-lookup"><span data-stu-id="5e851-119">`Disconnect-PSSession`: Disconnects a PSSession.</span></span>
- <span data-ttu-id="5e851-120">`Get-PSSession`: Hämtar PSSessions på den lokala datorn eller på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="5e851-120">`Get-PSSession`: Gets PSSessions on the local computer or on remote computers.</span></span>
- <span data-ttu-id="5e851-121">`Receive-PSSession`: Hämtar resultatet från kommandon som kördes i frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="5e851-121">`Receive-PSSession`: Gets the results of commands that ran in disconnected sessions.</span></span>
- <span data-ttu-id="5e851-122">`Invoke-Command`: **InDisconnectedSession** -parametern skapar en PSSession och kopplar från omedelbart.</span><span class="sxs-lookup"><span data-stu-id="5e851-122">`Invoke-Command`: **InDisconnectedSession** parameter creates a PSSession and disconnects immediately.</span></span>

## <a name="how-the-disconnected-sessions-feature-works"></a><span data-ttu-id="5e851-123">Så här fungerar funktionen frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="5e851-123">How the Disconnected Sessions feature works</span></span>

<span data-ttu-id="5e851-124">Från och med PowerShell 3,0 är PSSessions oberoende av de sessioner som de har skapats i.</span><span class="sxs-lookup"><span data-stu-id="5e851-124">Beginning in PowerShell 3.0, PSSessions are independent of the sessions in which they're created.</span></span> <span data-ttu-id="5e851-125">Aktiva PSSessions underhålls på fjärrdatorn eller **Server sidan** av anslutningen, även om sessionen där PSSession skapades är stängd och den ursprungliga datorn stängs av eller kopplas från nätverket.</span><span class="sxs-lookup"><span data-stu-id="5e851-125">Active PSSessions are maintained on the remote computer or **server-side** of the connection, even if the session in which the PSSession was created is closed and the originating computer is shut down or disconnected from the network.</span></span>

<span data-ttu-id="5e851-126">I PowerShell 2,0 tas PSSession bort från fjärrdatorn när den kopplas bort från den ursprungliga sessionen eller den session där den skapades.</span><span class="sxs-lookup"><span data-stu-id="5e851-126">In PowerShell 2.0, the PSSession is deleted from the remote computer when it's disconnected from the originating session or the session in which it was created ends.</span></span>

<span data-ttu-id="5e851-127">När du kopplar från en PSSession förblir PSSession aktiv och bevaras på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-127">When you disconnect a PSSession, the PSSession remains active and is maintained on the remote computer.</span></span> <span data-ttu-id="5e851-128">Sessionstillståndet ändras från att **köras** till **frånkopplat**.</span><span class="sxs-lookup"><span data-stu-id="5e851-128">The session state changes from **Running** to **Disconnected**.</span></span> <span data-ttu-id="5e851-129">Du kan återansluta till en frånkopplad PSSession från den aktuella sessionen eller från en annan session på samma dator, eller från en annan dator.</span><span class="sxs-lookup"><span data-stu-id="5e851-129">You can reconnect to a disconnected PSSession from the current session or from a different session on the same computer, or from a different computer.</span></span> <span data-ttu-id="5e851-130">Den fjärrdator som underhåller sessionen måste köras och vara ansluten till nätverket.</span><span class="sxs-lookup"><span data-stu-id="5e851-130">The remote computer that maintains the session must be running and be connected to the network.</span></span>

<span data-ttu-id="5e851-131">Kommandon i en frånkopplad PSSession fortsätter att köras utan avbrott på fjärrdatorn tills kommandot har slutförts eller när utdatabufferten fylls.</span><span class="sxs-lookup"><span data-stu-id="5e851-131">Commands in a disconnected PSSession continue to run uninterrupted on the remote computer until the command completes or the output buffer fills.</span></span> <span data-ttu-id="5e851-132">Om du vill förhindra att en fullständig utdatabuffert pausar ett kommando använder du parametern **OutputBufferingMode** i `Disconnect-PSSession` `New-PSSessionOption` cmdletarna,, eller `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="5e851-132">To prevent a full output buffer from suspending a command, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="5e851-133">Frånkopplade sessioner underhålls i frånkopplat läge på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-133">Disconnected sessions are maintained in the disconnected state on the remote computer.</span></span> <span data-ttu-id="5e851-134">De är tillgängliga så att du kan återansluta tills du tar bort PSSession, till exempel med hjälp av `Remove-PSSession` cmdleten eller tills tids gränsen för inaktivitet för PSSession går ut.</span><span class="sxs-lookup"><span data-stu-id="5e851-134">They're available for you to reconnect, until you delete the PSSession, such as by using the `Remove-PSSession` cmdlet, or until the idle timeout of the PSSession expires.</span></span> <span data-ttu-id="5e851-135">Du kan ändra tids gränsen för inaktivitet för en PSSession med hjälp av **IdleTimeoutSec** -eller **idleTimeout** -parametrarna för `Disconnect-PSSession` -, `New-PSSessionOption` -eller- `New-PSTransportOption` cmdlet: arna.</span><span class="sxs-lookup"><span data-stu-id="5e851-135">You can adjust the idle timeout of a PSSession by using the **IdleTimeoutSec** or **IdleTimeout** parameters of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="5e851-136">En annan användare kan ansluta till PSSessions som du har skapat, men endast om de kan ange de autentiseringsuppgifter som användes för att skapa sessionen eller använda `RunAs` autentiseringsuppgifterna för sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-136">Another user can connect to PSSessions that you created, but only if they can provide the credentials that were used to create the session, or use the `RunAs` credentials of the session configuration.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="5e851-137">Så här hämtar du PSSessions</span><span class="sxs-lookup"><span data-stu-id="5e851-137">How to get PSSessions</span></span>

<span data-ttu-id="5e851-138">Från och med PowerShell 3,0 `Get-PSSession` hämtar cmdlet: en PSSessions på den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="5e851-138">Beginning in PowerShell 3.0, the `Get-PSSession` cmdlet gets PSSessions on the local computer and remote computers.</span></span> <span data-ttu-id="5e851-139">Den kan också hämta PSSessions som har skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-139">It can also get PSSessions that were created in the current session.</span></span>

<span data-ttu-id="5e851-140">Om du vill hämta PSSessions på den lokala datorn eller fjärrdatorer använder du parametrarna **computername** eller **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="5e851-140">To get PSSessions on the local computer or remote computers, use the **ComputerName** or **ConnectionUri** parameters.</span></span> <span data-ttu-id="5e851-141">Utan parametrar `Get-PSSession` hämtar PSSession som skapats i den lokala sessionen, oavsett var de avslutas.</span><span class="sxs-lookup"><span data-stu-id="5e851-141">Without parameters, `Get-PSSession` gets PSSession that were created in the local session, regardless of where they terminate.</span></span>

<span data-ttu-id="5e851-142">Kom ihåg att leta efter dem på den dator där de befinner sig, det vill säga fjärrdatorn eller **Server sidan** när du hämtar PSSessions.</span><span class="sxs-lookup"><span data-stu-id="5e851-142">When getting PSSessions, remember to look for them on the computer on which they're maintained, that is, the remote or **server-side** computer.</span></span>

<span data-ttu-id="5e851-143">Om du till exempel skapar en PSSession till Server01-datorn hämtar du sessionen från Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-143">For example, if you create a PSSession to the Server01 computer, get the session from the Server01 computer.</span></span> <span data-ttu-id="5e851-144">Om du skapar en PSSession från en annan dator till den lokala datorn hämtar du sessionen från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-144">If you create a PSSession from another computer to the local computer, get the session from the local computer.</span></span>

<span data-ttu-id="5e851-145">Följande kommando sekvens visar hur `Get-PSSession` fungerar.</span><span class="sxs-lookup"><span data-stu-id="5e851-145">The following command sequence shows how `Get-PSSession` works.</span></span>

<span data-ttu-id="5e851-146">Det första kommandot skapar en session till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-146">The first command creates a session to the Server01 computer.</span></span> <span data-ttu-id="5e851-147">Sessionen finns på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-147">The session resides on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="5e851-148">För att hämta sessionen använder du parametern **computername** för `Get-PSSession` med värdet Server01.</span><span class="sxs-lookup"><span data-stu-id="5e851-148">To get the session, use the **ComputerName** parameter of `Get-PSSession` with a value of Server01.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="5e851-149">Om värdet för parametern **computername** för `Get-PSSession` är localhost, `Get-PSSession` hämtar PSSessions som slutar på och underhålls på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-149">If the value of the **ComputerName** parameter of `Get-PSSession` is localhost, `Get-PSSession` gets PSSessions that terminate at and are maintained on the local computer.</span></span> <span data-ttu-id="5e851-150">Den får inte PSSessions på Server01-datorn, även om de startades på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-150">It doesn't get PSSessions on the Server01 computer, even if they were started on the local computer.</span></span>

```powershell
Get-PSSession -ComputerName localhost
```

<span data-ttu-id="5e851-151">Använd cmdleten utan parametrar för att hämta sessioner som har skapats i den aktuella sessionen `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5e851-151">To get sessions that were created in the current session, use the `Get-PSSession` cmdlet without parameters.</span></span> <span data-ttu-id="5e851-152">I det här exemplet `Get-PSSession` hämtar PSSession som skapades i den aktuella sessionen och ansluter till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-152">In this example, `Get-PSSession` gets the PSSession that was created in the current session and connects to the Server01 computer.</span></span>

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a><span data-ttu-id="5e851-153">Koppla från sessioner</span><span class="sxs-lookup"><span data-stu-id="5e851-153">How to disconnect sessions</span></span>

<span data-ttu-id="5e851-154">Använd cmdleten om du vill koppla från en PSSession `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5e851-154">To disconnect a PSSession, use the `Disconnect-PSSession` cmdlet.</span></span> <span data-ttu-id="5e851-155">Om du vill identifiera PSSession använder du parametern **session** eller pipeline a PSSession från `New-PSSession` `Get-PSSession` cmdletarna eller `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5e851-155">To identify the PSSession, use the **Session** parameter, or pipeline a PSSession from the `New-PSSession` or `Get-PSSession` cmdlets to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="5e851-156">Följande kommando kopplar från PSSession till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-156">The following command disconnects the PSSession to the Server01 computer.</span></span>
<span data-ttu-id="5e851-157">Observera att värdet för egenskapen **State** är **frånkopplat** och att **tillgängligheten** är **ingen**.</span><span class="sxs-lookup"><span data-stu-id="5e851-157">Notice that the value of the **State** property is **Disconnected** and the **Availability** is **None**.</span></span>

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="5e851-158">Använd parametern **InDisconnectedSession** för cmdleten om du vill skapa en frånkopplad session `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="5e851-158">To create a disconnected session, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="5e851-159">Den skapar en session, startar kommandot och kopplar från omedelbart, innan kommandot kan returnera utdata.</span><span class="sxs-lookup"><span data-stu-id="5e851-159">It creates a session, starts the command, and disconnects immediately, before the command can return any output.</span></span>

<span data-ttu-id="5e851-160">Följande kommando kör ett `Get-WinEvent` kommando i en frånkopplad session på den fjärranslutna Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-160">The following command runs a `Get-WinEvent` command in a disconnected session on the Server02 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a><span data-ttu-id="5e851-161">Så här ansluter du till frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="5e851-161">How to connect to disconnected sessions</span></span>

<span data-ttu-id="5e851-162">Du kan ansluta till alla tillgängliga frånkopplade PSSession från sessionen där du skapade PSSession eller från andra sessioner på den lokala datorn eller på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="5e851-162">You can connect to any available disconnected PSSession from the session in which you created the PSSession or from other sessions on the local computer or other computers.</span></span>

<span data-ttu-id="5e851-163">Du kan skapa en PSSession, köra kommandon i PSSession, koppla från PSSession, stänga PowerShell och stänga av datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-163">You can create a PSSession, run commands in the PSSession, disconnect from the PSSession, close PowerShell, and shut down the computer.</span></span> <span data-ttu-id="5e851-164">Timmar senare kan du öppna en annan dator, Hämta PSSession, ansluta till den och hämta resultatet av de kommandon som kördes i PSSession när den kopplades från.</span><span class="sxs-lookup"><span data-stu-id="5e851-164">Hours later, you can open a different computer, get the PSSession, connect to it, and get the results of commands that ran in the PSSession while it was disconnected.</span></span> <span data-ttu-id="5e851-165">Sedan kan du köra fler kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-165">Then you can run more commands in the session.</span></span>

<span data-ttu-id="5e851-166">Använd cmdleten för att ansluta en frånkopplad PSSession `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5e851-166">To connect a disconnected PSSession, use the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="5e851-167">Använd parametrarna **computername** eller **ConnectionUri** för att identifiera PSSession eller pipeline a PSSession från `Get-PSSession` till `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5e851-167">Use the **ComputerName** or **ConnectionUri** parameters to identify the PSSession, or pipeline a PSSession from `Get-PSSession` to `Connect-PSSession`.</span></span>

<span data-ttu-id="5e851-168">Följande kommando hämtar sessionerna på den Server02 datorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-168">The following command gets the sessions on the Server02 computer.</span></span> <span data-ttu-id="5e851-169">Utdata innehåller två frånkopplade sessioner, som båda är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="5e851-169">The output includes two disconnected sessions, both of which are available.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="5e851-170">Följande kommando ansluter till Session2.</span><span class="sxs-lookup"><span data-stu-id="5e851-170">The following command connects to Session2.</span></span> <span data-ttu-id="5e851-171">PSSession är nu öppen och tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="5e851-171">The PSSession is now open and available.</span></span>

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a><span data-ttu-id="5e851-172">Så här hämtar du resultatet</span><span class="sxs-lookup"><span data-stu-id="5e851-172">How to get the results</span></span>

<span data-ttu-id="5e851-173">Använd cmdleten för att hämta resultatet av kommandon som kördes i en frånkopplad PSSession `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5e851-173">To get the results of commands that ran in a disconnected PSSession, use the `Receive-PSSession` cmdlet.</span></span>

<span data-ttu-id="5e851-174">Du kan använda `Receive-PSSession` i stället för att använda `Connect-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e851-174">You can use `Receive-PSSession` rather than using the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="5e851-175">Om sessionen redan är ansluten igen `Receive-PSSession` hämtar resultatet från kommandon som kördes när sessionen kopplades från.</span><span class="sxs-lookup"><span data-stu-id="5e851-175">If the session is already reconnected, `Receive-PSSession` gets the results of commands that ran when the session was disconnected.</span></span> <span data-ttu-id="5e851-176">Om PSSession fortfarande är frånkopplad `Receive-PSSession` ansluter du till den och hämtar sedan resultatet från kommandon som kördes medan den kopplades från.</span><span class="sxs-lookup"><span data-stu-id="5e851-176">If the PSSession is still disconnected, `Receive-PSSession` connects to it and then gets the results of commands that ran while it was disconnected.</span></span>

<span data-ttu-id="5e851-177">`Receive-PSSession` kan returnera resultatet i ett jobb (asynkront) eller till värd programmet (synkront).</span><span class="sxs-lookup"><span data-stu-id="5e851-177">`Receive-PSSession` can return the results in a job (asynchronously) or to the host program (synchronously).</span></span> <span data-ttu-id="5e851-178">Använd **mål** parametern för att välja **jobb** eller **värd**.</span><span class="sxs-lookup"><span data-stu-id="5e851-178">Use the **OutTarget** parameter to select **Job** or **Host**.</span></span> <span data-ttu-id="5e851-179">Standardvärdet är **Host**.</span><span class="sxs-lookup"><span data-stu-id="5e851-179">The default value is **Host**.</span></span> <span data-ttu-id="5e851-180">Men om kommandot som tas emot startades i den aktuella sessionen som ett **jobb** , returneras det som ett **jobb** som standard.</span><span class="sxs-lookup"><span data-stu-id="5e851-180">However, if the command that's being received was started in the current session as a **Job** , it's returned as a **Job** by default.</span></span>

<span data-ttu-id="5e851-181">Följande kommando använder `Receive-PSSession` cmdleten för att ansluta till PSSession på Server02-datorn och hämta resultatet från `Get-WinEvent` kommandot som kördes i Session3-sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-181">The following command uses the `Receive-PSSession` cmdlet to connect to the PSSession on the Server02 computer and get the results of the `Get-WinEvent` command that ran in the Session3 session.</span></span> <span data-ttu-id="5e851-182">Kommandot använder **mål** parametern för att hämta resultatet i ett **jobb**.</span><span class="sxs-lookup"><span data-stu-id="5e851-182">The command uses the **OutTarget** parameter to get the results in a **Job**.</span></span>

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

<span data-ttu-id="5e851-183">Använd cmdleten för att hämta jobbets resultat `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="5e851-183">To get the job's results, use the `Receive-Job` cmdlet.</span></span>

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a><span data-ttu-id="5e851-184">Egenskaper för tillstånd och tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="5e851-184">State and Availability properties</span></span>

<span data-ttu-id="5e851-185">Egenskaperna för **tillstånd** och **tillgänglighet** för en frånkopplad PSSession anger om sessionen är tillgänglig för att återansluta till den.</span><span class="sxs-lookup"><span data-stu-id="5e851-185">The **State** and **Availability** properties of a disconnected PSSession tell you whether the session is available for you to reconnect to it.</span></span>

<span data-ttu-id="5e851-186">När en PSSession är ansluten till den aktuella sessionen **öppnas** dess tillstånd och dess tillgänglighet är **tillgänglig**.</span><span class="sxs-lookup"><span data-stu-id="5e851-186">When a PSSession is connected to the current session, its state is **Opened** and its availability is **Available**.</span></span> <span data-ttu-id="5e851-187">När du kopplar från PSSession är PSSession-läget **frånkopplat** och dess tillgänglighet är **ingen**.</span><span class="sxs-lookup"><span data-stu-id="5e851-187">When you disconnect from the PSSession, the PSSession state is **Disconnected** and its availability is **None**.</span></span>

<span data-ttu-id="5e851-188">Värdet för egenskapen **State** är i förhållande till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-188">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="5e851-189">Värdet **frånkopplat** innebär att PSSession inte är ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-189">A value of **Disconnected** means that the PSSession isn't connected to the current session.</span></span> <span data-ttu-id="5e851-190">Men det betyder inte att PSSession är frånkopplad från alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="5e851-190">But, it doesn't mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="5e851-191">Den kan vara ansluten till en annan session.</span><span class="sxs-lookup"><span data-stu-id="5e851-191">It might be connected to a different session.</span></span>

<span data-ttu-id="5e851-192">Använd egenskapen **Availability** för att avgöra om du kan ansluta eller återansluta till PSSession.</span><span class="sxs-lookup"><span data-stu-id="5e851-192">To determine whether you can connect or reconnect to the PSSession, use the **Availability** property.</span></span> <span data-ttu-id="5e851-193">Värdet **none** anger att du kan ansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-193">A value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="5e851-194">Värdet **upptagen** anger att du inte kan ansluta till PSSession eftersom det är anslutet till en annan session.</span><span class="sxs-lookup"><span data-stu-id="5e851-194">A value of **Busy** indicates that you can't connect to the PSSession because it's connected to another session.</span></span>

<span data-ttu-id="5e851-195">Följande exempel körs i två PowerShell-sessioner på samma dator.</span><span class="sxs-lookup"><span data-stu-id="5e851-195">The following example is run in two PowerShell sessions on the same computer.</span></span>
<span data-ttu-id="5e851-196">Observera de ändrade värdena för egenskaperna **State** och **Availability** i varje session när PSSession är frånkopplad och Återansluten.</span><span class="sxs-lookup"><span data-stu-id="5e851-196">Note the changing values of the **State** and **Availability** properties in each session as the PSSession is disconnected and reconnected.</span></span>

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

<span data-ttu-id="5e851-197">Frånkopplade sessioner underhålls på fjärrdatorn tills du tar bort dem, till exempel med hjälp av `Remove-PSSession` cmdleten eller tids gränsen. Egenskapen **idleTimeout** för en PSSession bestämmer hur länge en frånkopplad session upprätthålls innan den tas bort.</span><span class="sxs-lookup"><span data-stu-id="5e851-197">Disconnected sessions are maintained on the remote computer until you delete them, such as by using the `Remove-PSSession` cmdlet, or they time out. The **IdleTimeout** property of a PSSession determines how long a disconnected session is maintained before it's deleted.</span></span>

<span data-ttu-id="5e851-198">PSSessions är inaktiva när **pulsslags tråden** inte får något svar.</span><span class="sxs-lookup"><span data-stu-id="5e851-198">PSSessions are idle when the **heartbeat thread** receives no response.</span></span>
<span data-ttu-id="5e851-199">Om du kopplar från en session blir den inaktiv och startar **idleTimeout** , även om kommandon fortfarande körs i den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-199">Disconnecting a session makes it idle and starts the **IdleTimeout** clock, even if commands are still running in the disconnected session.</span></span> <span data-ttu-id="5e851-200">I PowerShell anses frånkopplade sessioner vara aktiva, men inaktiva.</span><span class="sxs-lookup"><span data-stu-id="5e851-200">PowerShell considers disconnected sessions to be active, but idle.</span></span>

<span data-ttu-id="5e851-201">När du skapar och kopplar från sessioner kontrollerar du att tids gränsen för inaktivitet i PSSession är tillräckligt lång för att underhålla sessionen för dina behov, men inte så länge den förbrukar onödiga resurser på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-201">When creating and disconnecting sessions, verify that the idle timeout in the PSSession is long enough to maintain the session for your needs, but not so long that it consumes unnecessary resources on the remote computer.</span></span>

<span data-ttu-id="5e851-202">**IdleTimeoutMs** -egenskapen för sessionens konfiguration bestämmer tids gränsen för inaktivitet för sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-202">The **IdleTimeoutMs** property of the session configuration determines the default idle timeout of sessions that use the session configuration.</span></span> <span data-ttu-id="5e851-203">Du kan åsidosätta standardvärdet, men det värde som du använder får inte överskrida **MaxIdleTimeoutMs** -egenskapen för sessionens konfiguration.</span><span class="sxs-lookup"><span data-stu-id="5e851-203">You can override the default value, but the value that you use can't exceed the **MaxIdleTimeoutMs** property of the session configuration.</span></span>

<span data-ttu-id="5e851-204">Använd följande kommando format för att hitta värdet för **IdleTimeoutMs** -och **MaxIdleTimeoutMs** -värden för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-204">To find the value of the **IdleTimeoutMs** and **MaxIdleTimeoutMs** values of a session configuration, use the following command format.</span></span>

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

<span data-ttu-id="5e851-205">Du kan åsidosätta standardvärdet i konfigurationen av sessionen och ange tids gränsen för inaktivitet för en PSSession när du skapar en PSSession och när du kopplar från.</span><span class="sxs-lookup"><span data-stu-id="5e851-205">You can override the default value in the session configuration and set the idle timeout of a PSSession when you create a PSSession and when you disconnect.</span></span>

<span data-ttu-id="5e851-206">Om du är medlem i gruppen Administratörer på fjärrdatorn kan du skapa och ändra egenskaperna **IdleTimeoutMs** och **MaxIdleTimeoutMs** för sessionsinställningar.</span><span class="sxs-lookup"><span data-stu-id="5e851-206">If you're a member of the Administrators group on the remote computer, you can create and change the **IdleTimeoutMs** and **MaxIdleTimeoutMs** properties of session configurations.</span></span>

## <a name="idle-timeout-values"></a><span data-ttu-id="5e851-207">Timeout-värden för inaktivitet</span><span class="sxs-lookup"><span data-stu-id="5e851-207">Idle timeout values</span></span>

<span data-ttu-id="5e851-208">Timeout-värdet för inaktivitet för sessionsinställningar och sessionsinformation är i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="5e851-208">The idle timeout value of session configurations and session options is in milliseconds.</span></span> <span data-ttu-id="5e851-209">Timeout-värdet för inaktivitet i sessioner och konfigurations alternativ för sessioner är i sekunder.</span><span class="sxs-lookup"><span data-stu-id="5e851-209">The idle timeout value of sessions and session configuration options is in seconds.</span></span>

<span data-ttu-id="5e851-210">Du kan ange tids gränsen för inaktivitet för en PSSession när du skapar PSSession ( `New-PSSession` , `Invoke-Command` ) och när du kopplar från den ( `Disconnect-PSSession` ).</span><span class="sxs-lookup"><span data-stu-id="5e851-210">You can set the idle timeout of a PSSession when you create the PSSession (`New-PSSession`, `Invoke-Command`) and when you disconnect from it (`Disconnect-PSSession`).</span></span> <span data-ttu-id="5e851-211">Du kan dock inte ändra **idleTimeout** -värdet när du ansluter till PSSession ( `Connect-PSSession` ) eller hämta resultat ( `Receive-PSSession` ).</span><span class="sxs-lookup"><span data-stu-id="5e851-211">However, you can't change the **IdleTimeout** value when you connect to the PSSession (`Connect-PSSession`) or get results (`Receive-PSSession`).</span></span>

<span data-ttu-id="5e851-212">`Connect-PSSession` `Receive-PSSession` Cmdletarna och har en **SessionOption** -parameter som tar ett **SessionOption** -objekt, till exempel en som returneras av `New-PSSessionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e851-212">The `Connect-PSSession` and `Receive-PSSession` cmdlets have a **SessionOption** parameter that takes a **SessionOption** object, such as one returned by the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="5e851-213">**IdleTimeout** -värdet i **SessionOption** -objektet och **idleTimeout** -värdet i `$PSSessionOption` variabeln Preference ändrar inte värdet för **idleTimeout** för PSSession i ett- `Connect-PSSession` eller- `Receive-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="5e851-213">The **IdleTimeout** value in **SessionOption** object and the **IdleTimeout** value in the `$PSSessionOption` preference variable don't change the value of the **IdleTimeout** of the PSSession in a `Connect-PSSession` or `Receive-PSSession` command.</span></span>

<span data-ttu-id="5e851-214">Skapa en inställnings variabel om du vill skapa en PSSession med ett visst tids gräns värde för inaktivitet `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="5e851-214">To create a PSSession with a particular idle timeout value, create a `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="5e851-215">Ange värdet för **idleTimeout** -egenskapen till önskat värde (i millisekunder).</span><span class="sxs-lookup"><span data-stu-id="5e851-215">Set the value of the **IdleTimeout** property to the desired value (in milliseconds).</span></span>

<span data-ttu-id="5e851-216">När du skapar PSSessions prioriteras värdena i `$PSSessionOption` variabeln över värdena i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-216">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="5e851-217">Följande kommando anger till exempel en timeout för inaktivitet på 48 timmar:</span><span class="sxs-lookup"><span data-stu-id="5e851-217">For example, the following command sets an idle timeout of 48 hours:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

<span data-ttu-id="5e851-218">Om du vill skapa en PSSession med ett visst tids gräns värde för inaktivitet, använder du parametern **IdleTimeoutMSec** för `New-PSSessionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e851-218">To create a PSSession with a particular idle timeout value, use the **IdleTimeoutMSec** parameter of the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="5e851-219">Använd sedan alternativet session i värdet för parametern **SessionOption** i `New-PSSession` `Invoke-Command` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="5e851-219">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="5e851-220">Värdena som anges när du skapar sessionen prioriteras framför de värden som anges i `$PSSessionOption` variabeln Preference och konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-220">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="5e851-221">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-221">For example:</span></span>

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

<span data-ttu-id="5e851-222">Om du vill ändra tids gränsen för inaktivitet för en PSSession vid från koppling använder du parametern **IdleTimeoutSec** för `Disconnect-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e851-222">To change the idle timeout of a PSSession when disconnecting, use the **IdleTimeoutSec** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="5e851-223">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-223">For example:</span></span>

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

<span data-ttu-id="5e851-224">Om du vill skapa en sessionshantering med en viss tids gräns för inaktivitet och maximal tids gräns för inaktivitet använder du cmdleten **IdleTimeoutSec** och **MaxIdleTimeoutSec** `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="5e851-224">To create a session configuration with a particular idle timeout and maximum idle timeout, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="5e851-225">Använd sedan alternativet transport i värdet för parametern **TransportOption** i `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5e851-225">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="5e851-226">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-226">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="5e851-227">Om du vill ändra standard tids gränsen för inaktivitet och maximal tids gräns för inaktivitet för en session, använder du cmdleten **IdleTimeoutSec** och **MaxIdleTimeoutSec** `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="5e851-227">To change the default idle timeout and maximum idle timeout of a session configuration, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="5e851-228">Använd sedan alternativet transport i värdet för parametern **TransportOption** i `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5e851-228">Then, use the transport option in the value of the **TransportOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="5e851-229">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-229">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a><span data-ttu-id="5e851-230">Läge för buffring av utdata</span><span class="sxs-lookup"><span data-stu-id="5e851-230">Output buffering mode</span></span>

<span data-ttu-id="5e851-231">Utmatnings buffertens läge för en PSSession bestämmer hur kommandoutdata hanteras när utdatabufferten för PSSession är full.</span><span class="sxs-lookup"><span data-stu-id="5e851-231">The output buffering mode of a PSSession determines how command output is managed when the output buffer of the PSSession is full.</span></span>

<span data-ttu-id="5e851-232">I en frånkopplad session avgör utmatnings buffertens läge om kommandot fortsätter att köras medan sessionen kopplas från.</span><span class="sxs-lookup"><span data-stu-id="5e851-232">In a disconnected session, the output buffering mode effectively determines whether the command continues to run while the session is disconnected.</span></span>

<span data-ttu-id="5e851-233">Giltiga värden enligt följande:</span><span class="sxs-lookup"><span data-stu-id="5e851-233">The valid values as follows:</span></span>

- <span data-ttu-id="5e851-234">**Blockera**.</span><span class="sxs-lookup"><span data-stu-id="5e851-234">**Block**.</span></span> <span data-ttu-id="5e851-235">När utdatabufferten är full pausas körningen tills bufferten är klar.</span><span class="sxs-lookup"><span data-stu-id="5e851-235">When the output buffer is full, execution is suspended until the buffer is clear.</span></span> <span data-ttu-id="5e851-236">Standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="5e851-236">The default value.</span></span>
- <span data-ttu-id="5e851-237">**Släpp**.</span><span class="sxs-lookup"><span data-stu-id="5e851-237">**Drop**.</span></span> <span data-ttu-id="5e851-238">När utdatabufferten är full fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="5e851-238">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="5e851-239">När nya utdata skapas, ignoreras det äldsta resultatet.</span><span class="sxs-lookup"><span data-stu-id="5e851-239">As new output is generated, the oldest output is discarded.</span></span>

<span data-ttu-id="5e851-240">**Blockera** data bevarar data, men kan avbryta kommandot.</span><span class="sxs-lookup"><span data-stu-id="5e851-240">**Block** preserves data, but might interrupt the command.</span></span> <span data-ttu-id="5e851-241">Ett **Drop** -värde gör att kommandot kan slutföras, men data kan gå förlorade.</span><span class="sxs-lookup"><span data-stu-id="5e851-241">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="5e851-242">När du använder **Drop** -värdet dirigerar du om kommandots utdata till en fil på disk.</span><span class="sxs-lookup"><span data-stu-id="5e851-242">When using the **Drop** value, redirect the command output to a file on disk.</span></span> <span data-ttu-id="5e851-243">Det här värdet rekommenderas för frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="5e851-243">This value is recommended for disconnected sessions.</span></span>

<span data-ttu-id="5e851-244">**OutputBufferingMode** -egenskapen för sessionens konfiguration bestämmer standardutdata för buffring av sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-244">The **OutputBufferingMode** property of the session configuration determines the default output buffering mode of sessions that use the session configuration.</span></span>

<span data-ttu-id="5e851-245">Om du vill hitta en konfigurations värde för en **OutputBufferingMode** kan du använda något av följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="5e851-245">To find a session configuration's value of the **OutputBufferingMode** , you can use either of the following command formats:</span></span>

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

<span data-ttu-id="5e851-246">Du kan åsidosätta standardvärdet i konfigurationen av sessionen och ange ett PSSession när du skapar en PSSession när du kopplar från, och när du återansluter.</span><span class="sxs-lookup"><span data-stu-id="5e851-246">You can override the default value in the session configuration and set the output buffering mode of a PSSession when you create a PSSession, when you disconnect, and when you reconnect.</span></span>

<span data-ttu-id="5e851-247">Om du är medlem i gruppen Administratörer på fjärrdatorn kan du skapa och ändra buffrings läget för utdata i sessioner.</span><span class="sxs-lookup"><span data-stu-id="5e851-247">If you're a member of the Administrators group on the remote computer, you can create and change the output buffering mode of session configurations.</span></span>

<span data-ttu-id="5e851-248">Om du vill skapa en PSSession med ett utmatnings **Buffer-läge** , skapar du en `$PSSessionOption` Preference-variabel där värdet för egenskapen **OutputBufferingMode** är **Drop**.</span><span class="sxs-lookup"><span data-stu-id="5e851-248">To create a PSSession with an output buffering mode of **Drop** , create a `$PSSessionOption` preference variable in which the value of the **OutputBufferingMode** property is **Drop**.</span></span>

<span data-ttu-id="5e851-249">När du skapar PSSessions prioriteras värdena i `$PSSessionOption` variabeln över värdena i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-249">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="5e851-250">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-250">For example:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

<span data-ttu-id="5e851-251">Om du vill skapa en PSSession med ett utmatnings **Buffer-läge** , använder du parametern **OutputBufferingMode** för cmdlet: en för `New-PSSessionOption` att skapa ett session-alternativ med värdet **Drop**.</span><span class="sxs-lookup"><span data-stu-id="5e851-251">To create a PSSession with an output buffering mode of **Drop** , use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="5e851-252">Använd sedan alternativet session i värdet för parametern **SessionOption** i `New-PSSession` `Invoke-Command` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="5e851-252">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="5e851-253">Värdena som anges när du skapar sessionen prioriteras framför de värden som anges i `$PSSessionOption` variabeln Preference och konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="5e851-253">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="5e851-254">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-254">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

<span data-ttu-id="5e851-255">Om du vill ändra utdata buffer-läget för en PSSession vid från koppling använder du parametern **OutputBufferingMode** för `Disconnect-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e851-255">To change the output buffering mode of a PSSession when disconnecting, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="5e851-256">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-256">For example:</span></span>

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

<span data-ttu-id="5e851-257">Om du vill ändra utdata buffer-läget för en PSSession vid åter anslutning använder du parametern **OutputBufferingMode** för cmdlet: en `New-PSSessionOption` för att skapa ett session-alternativ med värdet **Drop**.</span><span class="sxs-lookup"><span data-stu-id="5e851-257">To change the output buffering mode of a PSSession when reconnecting, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="5e851-258">Använd sedan alternativet session i värdet för parametern **SessionOption** i `Connect-PSSession` eller `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5e851-258">Then, use the session option in the value of the **SessionOption** parameter of `Connect-PSSession` or `Receive-PSSession`.</span></span>

<span data-ttu-id="5e851-259">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-259">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

<span data-ttu-id="5e851-260">Om du vill skapa en konfiguration av sessionen med ett utmatnings sätt **som är** förvalt, använder du parametern **OutputBufferingMode** för `New-PSTransportOption` cmdleten för att skapa ett transport alternativ objekt med värdet **Drop**.</span><span class="sxs-lookup"><span data-stu-id="5e851-260">To create a session configuration with a default output buffering mode of **Drop** , use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option object with a value of **Drop**.</span></span> <span data-ttu-id="5e851-261">Använd sedan alternativet transport i värdet för parametern **TransportOption** i `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5e851-261">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="5e851-262">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-262">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="5e851-263">Om du vill ändra standard läget för buffring av utdata för en session, använder du parametern **OutputBufferingMode** för `New-PSTransportOption` cmdlet: en för att skapa ett transport alternativ med värdet **Drop**.</span><span class="sxs-lookup"><span data-stu-id="5e851-263">To change the default output buffering mode of a session configuration, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option with a value of **Drop**.</span></span> <span data-ttu-id="5e851-264">Använd sedan alternativet transport i värdet för parametern **SessionOption** i `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5e851-264">Then, use the Transport option in the value of the **SessionOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="5e851-265">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5e851-265">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a><span data-ttu-id="5e851-266">Koppla från loopback-sessioner</span><span class="sxs-lookup"><span data-stu-id="5e851-266">Disconnecting loopback sessions</span></span>

<span data-ttu-id="5e851-267">Loopback-sessioner, eller lokala sessioner, är PSSessions som kommer från och slutar på samma dator.</span><span class="sxs-lookup"><span data-stu-id="5e851-267">Loopback sessions, or local sessions, are PSSessions that originate and terminate on the same computer.</span></span> <span data-ttu-id="5e851-268">Precis som andra PSSessions underhålls aktiva loopback-sessioner på datorn i Fjärrslutpunkten av anslutningen (den lokala datorn) så att du kan koppla från och återansluta till loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="5e851-268">Like other PSSessions, active loopback sessions are maintained on the computer on the remote end of the connection (the local computer), so you can disconnect from and reconnect to loopback sessions.</span></span>

<span data-ttu-id="5e851-269">Som standard skapas loopback-sessioner med en nätverks säkerhets-token som inte tillåter att kommandon körs i sessionen för att få åtkomst till andra datorer.</span><span class="sxs-lookup"><span data-stu-id="5e851-269">By default, loopback sessions are created with a network security token that doesn't permit commands run in the session to access other computers.</span></span> <span data-ttu-id="5e851-270">Du kan återansluta till loopback-sessioner som har en nätverks säkerhets-token från valfri session på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="5e851-270">You can reconnect to loopback sessions that have a network security token from any session on the local computer or a remote computer.</span></span>

<span data-ttu-id="5e851-271">Men om du använder parametern **EnableNetworkAccess** i `New-PSSession` `Enter-PSSession` cmdleten, eller, `Invoke-Command` skapas loopback-sessionen med en interaktiv säkerhetstoken.</span><span class="sxs-lookup"><span data-stu-id="5e851-271">However, if you use the **EnableNetworkAccess** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlet, the loopback session is created with an interactive security token.</span></span> <span data-ttu-id="5e851-272">Den interaktiva token gör det möjligt att köra kommandon som körs i loopback-sessionen för att hämta data från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="5e851-272">The interactive token enables commands that run in the loopback session to get data from other computers.</span></span>

<span data-ttu-id="5e851-273">Du kan koppla från loopback-sessioner med interaktiva token och sedan återansluta till dem från samma session eller en annan session på samma dator.</span><span class="sxs-lookup"><span data-stu-id="5e851-273">You can disconnect loopback sessions with interactive tokens and then reconnect to them from the same session or a different session on the same computer.</span></span>
<span data-ttu-id="5e851-274">Men för att förhindra obehörig åtkomst kan du återansluta till loopback-sessioner med interaktiva tokens enbart från den dator där de skapades.</span><span class="sxs-lookup"><span data-stu-id="5e851-274">However, to prevent malicious access, you can reconnect to loopback sessions with interactive tokens only from the computer on which they were created.</span></span>

## <a name="waiting-for-jobs-in-disconnected-sessions"></a><span data-ttu-id="5e851-275">Väntar på jobb i frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="5e851-275">Waiting for jobs in disconnected sessions</span></span>

<span data-ttu-id="5e851-276">`Wait-Job`Cmdleten väntar tills ett jobb har slutförts och återgår sedan till kommando tolken eller nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="5e851-276">The `Wait-Job` cmdlet waits until a job completes and then returns to the command prompt or the next command.</span></span> <span data-ttu-id="5e851-277">Som standard `Wait-Job` returneras om sessionen där ett jobb körs är frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="5e851-277">By default, `Wait-Job` returns if the session in which a job is running is disconnected.</span></span> <span data-ttu-id="5e851-278">Om du vill dirigera `Wait-Job` cmdleten till att vänta tills sessionen har återanslutits använder du parametern **Force** i **öppnings** läge.</span><span class="sxs-lookup"><span data-stu-id="5e851-278">To direct the `Wait-Job` cmdlet to wait until the session is reconnected, in the **Opened** state, use the **Force** parameter.</span></span> <span data-ttu-id="5e851-279">Mer information finns i [wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span><span class="sxs-lookup"><span data-stu-id="5e851-279">For more information, see [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span></span>

## <a name="robust-sessions-and-unintentional-disconnection"></a><span data-ttu-id="5e851-280">Robusta sessioner och oavsiktlig från koppling</span><span class="sxs-lookup"><span data-stu-id="5e851-280">Robust sessions and unintentional disconnection</span></span>

<span data-ttu-id="5e851-281">En PSSession kan oavsiktligt kopplas från på grund av ett dator haveri eller nätverks avbrott.</span><span class="sxs-lookup"><span data-stu-id="5e851-281">A PSSession might be unintentionally disconnected because of a computer failure or network outage.</span></span> <span data-ttu-id="5e851-282">PowerShell försöker återställa PSSession, men dess framgång beror på orsakens allvarlighets grad och varaktighet.</span><span class="sxs-lookup"><span data-stu-id="5e851-282">PowerShell attempts to recover the PSSession, but its success depends upon the severity and duration of the cause.</span></span>

<span data-ttu-id="5e851-283">Statusen för en oavsiktligt frånkopplad PSSession kan vara **bruten** eller **stängd** , men den kan också vara **frånkopplad**.</span><span class="sxs-lookup"><span data-stu-id="5e851-283">The state of an unintentionally disconnected PSSession might be **Broken** or **Closed** , but it might also be **Disconnected**.</span></span> <span data-ttu-id="5e851-284">Om värdet för **State** är **frånkopplat** kan du använda samma metoder för att hantera PSSession på samma sätt som om sessionen kopplades från avsiktligt.</span><span class="sxs-lookup"><span data-stu-id="5e851-284">If the value of **State** is **Disconnected** , you can use the same techniques to manage the PSSession as you would if the session were disconnected intentionally.</span></span> <span data-ttu-id="5e851-285">Du kan till exempel använda `Connect-PSSession` cmdleten för att återansluta till sessionen och `Receive-PSSession` cmdleten för att få resultat från kommandon som kördes medan sessionen kopplades från.</span><span class="sxs-lookup"><span data-stu-id="5e851-285">For example, you can use the `Connect-PSSession` cmdlet to reconnect to the session and the `Receive-PSSession` cmdlet to get results of commands that ran while the session was disconnected.</span></span>

<span data-ttu-id="5e851-286">Om du stänger (avslutar) sessionen där en PSSession skapades medan kommandon körs i PSSession, underhåller PowerShell PSSession i **frånkopplat** läge på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="5e851-286">If you close (exit) the session in which a PSSession was created while commands are running in the PSSession, PowerShell maintains the PSSession in the **Disconnected** state on the remote computer.</span></span> <span data-ttu-id="5e851-287">Om du stänger (avslutar) sessionen där en PSSession skapades men inga kommandon körs i PSSession, försöker inte PowerShell underhålla PSSession.</span><span class="sxs-lookup"><span data-stu-id="5e851-287">If you close (exit) the session in which a PSSession was created, but no commands are running in the PSSession, PowerShell doesn't attempt to maintain the PSSession.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e851-288">Se även</span><span class="sxs-lookup"><span data-stu-id="5e851-288">See also</span></span>

[<span data-ttu-id="5e851-289">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="5e851-289">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="5e851-290">about_Remote</span><span class="sxs-lookup"><span data-stu-id="5e851-290">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="5e851-291">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="5e851-291">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="5e851-292">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="5e851-292">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="5e851-293">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="5e851-293">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="5e851-294">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="5e851-294">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="5e851-295">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="5e851-295">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="5e851-296">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="5e851-296">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="5e851-297">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="5e851-297">Receive-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[<span data-ttu-id="5e851-298">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="5e851-298">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
