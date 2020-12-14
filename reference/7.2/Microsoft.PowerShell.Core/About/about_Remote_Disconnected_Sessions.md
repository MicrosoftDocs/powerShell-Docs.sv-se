---
description: Förklarar hur du kopplar från och återansluter till en PowerShell-session (PSSession).
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 0756e110b1058915f6280e2ea59ee915bedb2c75
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708430"
---
# <a name="about-remote-disconnected-sessions"></a><span data-ttu-id="6333a-103">Om fjärranslutna sessioner</span><span class="sxs-lookup"><span data-stu-id="6333a-103">About Remote Disconnected Sessions</span></span>

## <a name="short-description"></a><span data-ttu-id="6333a-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="6333a-104">Short description</span></span>

<span data-ttu-id="6333a-105">Förklarar hur du kopplar från och återansluter till en PowerShell-session (PSSession).</span><span class="sxs-lookup"><span data-stu-id="6333a-105">Explains how to disconnect and reconnect to a PowerShell Session (PSSession).</span></span>

## <a name="long-description"></a><span data-ttu-id="6333a-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="6333a-106">Long description</span></span>

<span data-ttu-id="6333a-107">Från och med PowerShell 3,0 kan du koppla från en PSSession och återansluta till PSSession på samma dator eller en annan dator.</span><span class="sxs-lookup"><span data-stu-id="6333a-107">Beginning in PowerShell 3.0, you can disconnect from a PSSession and reconnect to the PSSession on the same computer or a different computer.</span></span> <span data-ttu-id="6333a-108">Sessionstillståndet upprätthålls och kommandon i PSSession fortsätter att köras medan sessionen kopplas från.</span><span class="sxs-lookup"><span data-stu-id="6333a-108">The session state is maintained and commands in the PSSession continue to run while the session is disconnected.</span></span>

<span data-ttu-id="6333a-109">Funktionen frånkopplade sessioner är bara tillgänglig när fjärrdatorn kör PowerShell 3,0 eller en senare version.</span><span class="sxs-lookup"><span data-stu-id="6333a-109">The Disconnected Sessions feature is only available when the remote computer is running PowerShell 3.0 or a later version.</span></span>

<span data-ttu-id="6333a-110">Med funktionen frånkopplade sessioner kan du stänga sessionen där en PSSession skapades, och till och med stänga PowerShell och stänga av datorn, utan att avbryta kommandon som körs i PSSession.</span><span class="sxs-lookup"><span data-stu-id="6333a-110">The Disconnected Sessions feature allows you to close the session in which a PSSession was created, and even close PowerShell, and shut down the computer, without disrupting commands running in the PSSession.</span></span> <span data-ttu-id="6333a-111">Frånkopplade sessioner är användbara för att köra kommandon som tar lång tid att slutföra och ger den tid och den flexibilitet som IT-proffs kräver.</span><span class="sxs-lookup"><span data-stu-id="6333a-111">Disconnected sessions are useful for running commands that take an extended time to complete, and provides the time and device flexibility that IT professionals require.</span></span>

<span data-ttu-id="6333a-112">Du kan inte koppla från en interaktiv session som har startats med hjälp av `Enter-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6333a-112">You can't disconnect from an interactive session that is started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="6333a-113">Du kan använda frånkopplade sessioner för att hantera PSSessions som frånkopplats oavsiktligt på grund av en dators eller ett nätverks avbrott.</span><span class="sxs-lookup"><span data-stu-id="6333a-113">You can use disconnected sessions to manage PSSessions that were disconnected unintentionally as the result of a computer or network outage.</span></span>

<span data-ttu-id="6333a-114">I verkligheten kan du använda funktionen frånkopplade sessioner för att lösa ett problem, förvandla din uppmärksamhet till ett problem med högre prioritet och sedan återuppta arbetet med lösningen, även på en annan dator på en annan plats.</span><span class="sxs-lookup"><span data-stu-id="6333a-114">In real-world use, the Disconnected Sessions feature allows you to begin solving a problem, turn your attention to a higher priority issue, and then resume work on the solution, even on a different computer in a different location.</span></span>

## <a name="disconnected-session-cmdlets"></a><span data-ttu-id="6333a-115">Cmdletar för frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="6333a-115">Disconnected session cmdlets</span></span>

<span data-ttu-id="6333a-116">Följande cmdletar stöder funktionen frånkopplade sessioner:</span><span class="sxs-lookup"><span data-stu-id="6333a-116">The following cmdlets support the Disconnected Sessions feature:</span></span>

- <span data-ttu-id="6333a-117">`Connect-PSSession`: Ansluter till en frånkopplad PSSession.</span><span class="sxs-lookup"><span data-stu-id="6333a-117">`Connect-PSSession`: Connects to a disconnected PSSession.</span></span>
- <span data-ttu-id="6333a-118">`Disconnect-PSSession`: Kopplar från en PSSession.</span><span class="sxs-lookup"><span data-stu-id="6333a-118">`Disconnect-PSSession`: Disconnects a PSSession.</span></span>
- <span data-ttu-id="6333a-119">`Get-PSSession`: Hämtar PSSessions på den lokala datorn eller på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="6333a-119">`Get-PSSession`: Gets PSSessions on the local computer or on remote computers.</span></span>
- <span data-ttu-id="6333a-120">`Receive-PSSession`: Hämtar resultatet från kommandon som kördes i frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="6333a-120">`Receive-PSSession`: Gets the results of commands that ran in disconnected sessions.</span></span>
- <span data-ttu-id="6333a-121">`Invoke-Command`: **InDisconnectedSession** -parametern skapar en PSSession och kopplar från omedelbart.</span><span class="sxs-lookup"><span data-stu-id="6333a-121">`Invoke-Command`: **InDisconnectedSession** parameter creates a PSSession and disconnects immediately.</span></span>

## <a name="how-the-disconnected-sessions-feature-works"></a><span data-ttu-id="6333a-122">Så här fungerar funktionen frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="6333a-122">How the Disconnected Sessions feature works</span></span>

<span data-ttu-id="6333a-123">Från och med PowerShell 3,0 är PSSessions oberoende av de sessioner som de har skapats i.</span><span class="sxs-lookup"><span data-stu-id="6333a-123">Beginning in PowerShell 3.0, PSSessions are independent of the sessions in which they're created.</span></span> <span data-ttu-id="6333a-124">Aktiva PSSessions underhålls på fjärrdatorn eller **Server sidan** av anslutningen, även om sessionen där PSSession skapades är stängd och den ursprungliga datorn stängs av eller kopplas från nätverket.</span><span class="sxs-lookup"><span data-stu-id="6333a-124">Active PSSessions are maintained on the remote computer or **server-side** of the connection, even if the session in which the PSSession was created is closed and the originating computer is shut down or disconnected from the network.</span></span>

<span data-ttu-id="6333a-125">I PowerShell 2,0 tas PSSession bort från fjärrdatorn när den kopplas bort från den ursprungliga sessionen eller den session där den skapades.</span><span class="sxs-lookup"><span data-stu-id="6333a-125">In PowerShell 2.0, the PSSession is deleted from the remote computer when it's disconnected from the originating session or the session in which it was created ends.</span></span>

<span data-ttu-id="6333a-126">När du kopplar från en PSSession förblir PSSession aktiv och bevaras på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-126">When you disconnect a PSSession, the PSSession remains active and is maintained on the remote computer.</span></span> <span data-ttu-id="6333a-127">Sessionstillståndet ändras från att **köras** till **frånkopplat**.</span><span class="sxs-lookup"><span data-stu-id="6333a-127">The session state changes from **Running** to **Disconnected**.</span></span> <span data-ttu-id="6333a-128">Du kan återansluta till en frånkopplad PSSession från den aktuella sessionen eller från en annan session på samma dator, eller från en annan dator.</span><span class="sxs-lookup"><span data-stu-id="6333a-128">You can reconnect to a disconnected PSSession from the current session or from a different session on the same computer, or from a different computer.</span></span> <span data-ttu-id="6333a-129">Den fjärrdator som underhåller sessionen måste köras och vara ansluten till nätverket.</span><span class="sxs-lookup"><span data-stu-id="6333a-129">The remote computer that maintains the session must be running and be connected to the network.</span></span>

<span data-ttu-id="6333a-130">Kommandon i en frånkopplad PSSession fortsätter att köras utan avbrott på fjärrdatorn tills kommandot har slutförts eller när utdatabufferten fylls.</span><span class="sxs-lookup"><span data-stu-id="6333a-130">Commands in a disconnected PSSession continue to run uninterrupted on the remote computer until the command completes or the output buffer fills.</span></span> <span data-ttu-id="6333a-131">Om du vill förhindra att en fullständig utdatabuffert pausar ett kommando använder du parametern **OutputBufferingMode** i `Disconnect-PSSession` `New-PSSessionOption` cmdletarna,, eller `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="6333a-131">To prevent a full output buffer from suspending a command, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="6333a-132">Frånkopplade sessioner underhålls i frånkopplat läge på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-132">Disconnected sessions are maintained in the disconnected state on the remote computer.</span></span> <span data-ttu-id="6333a-133">De är tillgängliga så att du kan återansluta tills du tar bort PSSession, till exempel med hjälp av `Remove-PSSession` cmdleten eller tills tids gränsen för inaktivitet för PSSession går ut.</span><span class="sxs-lookup"><span data-stu-id="6333a-133">They're available for you to reconnect, until you delete the PSSession, such as by using the `Remove-PSSession` cmdlet, or until the idle timeout of the PSSession expires.</span></span> <span data-ttu-id="6333a-134">Du kan ändra tids gränsen för inaktivitet för en PSSession med hjälp av **IdleTimeoutSec** -eller **idleTimeout** -parametrarna för `Disconnect-PSSession` -, `New-PSSessionOption` -eller- `New-PSTransportOption` cmdlet: arna.</span><span class="sxs-lookup"><span data-stu-id="6333a-134">You can adjust the idle timeout of a PSSession by using the **IdleTimeoutSec** or **IdleTimeout** parameters of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="6333a-135">En annan användare kan ansluta till PSSessions som du har skapat, men endast om de kan ange de autentiseringsuppgifter som användes för att skapa sessionen eller använda `RunAs` autentiseringsuppgifterna för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-135">Another user can connect to PSSessions that you created, but only if they can provide the credentials that were used to create the session, or use the `RunAs` credentials of the session configuration.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="6333a-136">Så här hämtar du PSSessions</span><span class="sxs-lookup"><span data-stu-id="6333a-136">How to get PSSessions</span></span>

<span data-ttu-id="6333a-137">Från och med PowerShell 3,0 `Get-PSSession` hämtar cmdlet: en PSSessions på den lokala datorn och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="6333a-137">Beginning in PowerShell 3.0, the `Get-PSSession` cmdlet gets PSSessions on the local computer and remote computers.</span></span> <span data-ttu-id="6333a-138">Den kan också hämta PSSessions som har skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-138">It can also get PSSessions that were created in the current session.</span></span>

<span data-ttu-id="6333a-139">Om du vill hämta PSSessions på den lokala datorn eller fjärrdatorer använder du parametrarna **computername** eller **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="6333a-139">To get PSSessions on the local computer or remote computers, use the **ComputerName** or **ConnectionUri** parameters.</span></span> <span data-ttu-id="6333a-140">Utan parametrar `Get-PSSession` hämtar PSSession som skapats i den lokala sessionen, oavsett var de avslutas.</span><span class="sxs-lookup"><span data-stu-id="6333a-140">Without parameters, `Get-PSSession` gets PSSession that were created in the local session, regardless of where they terminate.</span></span>

<span data-ttu-id="6333a-141">Kom ihåg att leta efter dem på den dator där de befinner sig, det vill säga fjärrdatorn eller **Server sidan** när du hämtar PSSessions.</span><span class="sxs-lookup"><span data-stu-id="6333a-141">When getting PSSessions, remember to look for them on the computer on which they're maintained, that is, the remote or **server-side** computer.</span></span>

<span data-ttu-id="6333a-142">Om du till exempel skapar en PSSession till Server01-datorn hämtar du sessionen från Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-142">For example, if you create a PSSession to the Server01 computer, get the session from the Server01 computer.</span></span> <span data-ttu-id="6333a-143">Om du skapar en PSSession från en annan dator till den lokala datorn hämtar du sessionen från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-143">If you create a PSSession from another computer to the local computer, get the session from the local computer.</span></span>

<span data-ttu-id="6333a-144">Följande kommando sekvens visar hur `Get-PSSession` fungerar.</span><span class="sxs-lookup"><span data-stu-id="6333a-144">The following command sequence shows how `Get-PSSession` works.</span></span>

<span data-ttu-id="6333a-145">Det första kommandot skapar en session till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-145">The first command creates a session to the Server01 computer.</span></span> <span data-ttu-id="6333a-146">Sessionen finns på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-146">The session resides on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="6333a-147">För att hämta sessionen använder du parametern **computername** för `Get-PSSession` med värdet Server01.</span><span class="sxs-lookup"><span data-stu-id="6333a-147">To get the session, use the **ComputerName** parameter of `Get-PSSession` with a value of Server01.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="6333a-148">Om värdet för parametern **computername** för `Get-PSSession` är localhost, `Get-PSSession` hämtar PSSessions som slutar på och underhålls på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-148">If the value of the **ComputerName** parameter of `Get-PSSession` is localhost, `Get-PSSession` gets PSSessions that terminate at and are maintained on the local computer.</span></span> <span data-ttu-id="6333a-149">Den får inte PSSessions på Server01-datorn, även om de startades på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-149">It doesn't get PSSessions on the Server01 computer, even if they were started on the local computer.</span></span>

```powershell
Get-PSSession -ComputerName localhost
```

<span data-ttu-id="6333a-150">Använd cmdleten utan parametrar för att hämta sessioner som har skapats i den aktuella sessionen `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6333a-150">To get sessions that were created in the current session, use the `Get-PSSession` cmdlet without parameters.</span></span> <span data-ttu-id="6333a-151">I det här exemplet `Get-PSSession` hämtar PSSession som skapades i den aktuella sessionen och ansluter till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-151">In this example, `Get-PSSession` gets the PSSession that was created in the current session and connects to the Server01 computer.</span></span>

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a><span data-ttu-id="6333a-152">Koppla från sessioner</span><span class="sxs-lookup"><span data-stu-id="6333a-152">How to disconnect sessions</span></span>

<span data-ttu-id="6333a-153">Använd cmdleten om du vill koppla från en PSSession `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6333a-153">To disconnect a PSSession, use the `Disconnect-PSSession` cmdlet.</span></span> <span data-ttu-id="6333a-154">Om du vill identifiera PSSession använder du parametern **session** eller pipeline a PSSession från `New-PSSession` `Get-PSSession` cmdletarna eller `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6333a-154">To identify the PSSession, use the **Session** parameter, or pipeline a PSSession from the `New-PSSession` or `Get-PSSession` cmdlets to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="6333a-155">Följande kommando kopplar från PSSession till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-155">The following command disconnects the PSSession to the Server01 computer.</span></span>
<span data-ttu-id="6333a-156">Observera att värdet för egenskapen **State** är **frånkopplat** och att **tillgängligheten** är **ingen**.</span><span class="sxs-lookup"><span data-stu-id="6333a-156">Notice that the value of the **State** property is **Disconnected** and the **Availability** is **None**.</span></span>

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="6333a-157">Använd parametern **InDisconnectedSession** för cmdleten om du vill skapa en frånkopplad session `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="6333a-157">To create a disconnected session, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="6333a-158">Den skapar en session, startar kommandot och kopplar från omedelbart, innan kommandot kan returnera utdata.</span><span class="sxs-lookup"><span data-stu-id="6333a-158">It creates a session, starts the command, and disconnects immediately, before the command can return any output.</span></span>

<span data-ttu-id="6333a-159">Följande kommando kör ett `Get-WinEvent` kommando i en frånkopplad session på den fjärranslutna Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-159">The following command runs a `Get-WinEvent` command in a disconnected session on the Server02 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a><span data-ttu-id="6333a-160">Så här ansluter du till frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="6333a-160">How to connect to disconnected sessions</span></span>

<span data-ttu-id="6333a-161">Du kan ansluta till alla tillgängliga frånkopplade PSSession från sessionen där du skapade PSSession eller från andra sessioner på den lokala datorn eller på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="6333a-161">You can connect to any available disconnected PSSession from the session in which you created the PSSession or from other sessions on the local computer or other computers.</span></span>

<span data-ttu-id="6333a-162">Du kan skapa en PSSession, köra kommandon i PSSession, koppla från PSSession, stänga PowerShell och stänga av datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-162">You can create a PSSession, run commands in the PSSession, disconnect from the PSSession, close PowerShell, and shut down the computer.</span></span> <span data-ttu-id="6333a-163">Timmar senare kan du öppna en annan dator, Hämta PSSession, ansluta till den och hämta resultatet av de kommandon som kördes i PSSession när den kopplades från.</span><span class="sxs-lookup"><span data-stu-id="6333a-163">Hours later, you can open a different computer, get the PSSession, connect to it, and get the results of commands that ran in the PSSession while it was disconnected.</span></span> <span data-ttu-id="6333a-164">Sedan kan du köra fler kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-164">Then you can run more commands in the session.</span></span>

<span data-ttu-id="6333a-165">Använd cmdleten för att ansluta en frånkopplad PSSession `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6333a-165">To connect a disconnected PSSession, use the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="6333a-166">Använd parametrarna **computername** eller **ConnectionUri** för att identifiera PSSession eller pipeline a PSSession från `Get-PSSession` till `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6333a-166">Use the **ComputerName** or **ConnectionUri** parameters to identify the PSSession, or pipeline a PSSession from `Get-PSSession` to `Connect-PSSession`.</span></span>

<span data-ttu-id="6333a-167">Följande kommando hämtar sessionerna på den Server02 datorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-167">The following command gets the sessions on the Server02 computer.</span></span> <span data-ttu-id="6333a-168">Utdata innehåller två frånkopplade sessioner, som båda är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="6333a-168">The output includes two disconnected sessions, both of which are available.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="6333a-169">Följande kommando ansluter till Session2.</span><span class="sxs-lookup"><span data-stu-id="6333a-169">The following command connects to Session2.</span></span> <span data-ttu-id="6333a-170">PSSession är nu öppen och tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="6333a-170">The PSSession is now open and available.</span></span>

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a><span data-ttu-id="6333a-171">Så här hämtar du resultatet</span><span class="sxs-lookup"><span data-stu-id="6333a-171">How to get the results</span></span>

<span data-ttu-id="6333a-172">Använd cmdleten för att hämta resultatet av kommandon som kördes i en frånkopplad PSSession `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6333a-172">To get the results of commands that ran in a disconnected PSSession, use the `Receive-PSSession` cmdlet.</span></span>

<span data-ttu-id="6333a-173">Du kan använda `Receive-PSSession` i stället för att använda `Connect-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6333a-173">You can use `Receive-PSSession` rather than using the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="6333a-174">Om sessionen redan är ansluten igen `Receive-PSSession` hämtar resultatet från kommandon som kördes när sessionen kopplades från.</span><span class="sxs-lookup"><span data-stu-id="6333a-174">If the session is already reconnected, `Receive-PSSession` gets the results of commands that ran when the session was disconnected.</span></span> <span data-ttu-id="6333a-175">Om PSSession fortfarande är frånkopplad `Receive-PSSession` ansluter du till den och hämtar sedan resultatet från kommandon som kördes medan den kopplades från.</span><span class="sxs-lookup"><span data-stu-id="6333a-175">If the PSSession is still disconnected, `Receive-PSSession` connects to it and then gets the results of commands that ran while it was disconnected.</span></span>

<span data-ttu-id="6333a-176">`Receive-PSSession` kan returnera resultatet i ett jobb (asynkront) eller till värd programmet (synkront).</span><span class="sxs-lookup"><span data-stu-id="6333a-176">`Receive-PSSession` can return the results in a job (asynchronously) or to the host program (synchronously).</span></span> <span data-ttu-id="6333a-177">Använd **mål** parametern för att välja **jobb** eller **värd**.</span><span class="sxs-lookup"><span data-stu-id="6333a-177">Use the **OutTarget** parameter to select **Job** or **Host**.</span></span> <span data-ttu-id="6333a-178">Standardvärdet är **Host**.</span><span class="sxs-lookup"><span data-stu-id="6333a-178">The default value is **Host**.</span></span> <span data-ttu-id="6333a-179">Men om kommandot som tas emot startades i den aktuella sessionen som ett **jobb**, returneras det som ett **jobb** som standard.</span><span class="sxs-lookup"><span data-stu-id="6333a-179">However, if the command that's being received was started in the current session as a **Job**, it's returned as a **Job** by default.</span></span>

<span data-ttu-id="6333a-180">Följande kommando använder `Receive-PSSession` cmdleten för att ansluta till PSSession på Server02-datorn och hämta resultatet från `Get-WinEvent` kommandot som kördes i Session3-sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-180">The following command uses the `Receive-PSSession` cmdlet to connect to the PSSession on the Server02 computer and get the results of the `Get-WinEvent` command that ran in the Session3 session.</span></span> <span data-ttu-id="6333a-181">Kommandot använder **mål** parametern för att hämta resultatet i ett **jobb**.</span><span class="sxs-lookup"><span data-stu-id="6333a-181">The command uses the **OutTarget** parameter to get the results in a **Job**.</span></span>

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

<span data-ttu-id="6333a-182">Använd cmdleten för att hämta jobbets resultat `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="6333a-182">To get the job's results, use the `Receive-Job` cmdlet.</span></span>

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

## <a name="state-and-availability-properties"></a><span data-ttu-id="6333a-183">Egenskaper för tillstånd och tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="6333a-183">State and Availability properties</span></span>

<span data-ttu-id="6333a-184">Egenskaperna för **tillstånd** och **tillgänglighet** för en frånkopplad PSSession anger om sessionen är tillgänglig för att återansluta till den.</span><span class="sxs-lookup"><span data-stu-id="6333a-184">The **State** and **Availability** properties of a disconnected PSSession tell you whether the session is available for you to reconnect to it.</span></span>

<span data-ttu-id="6333a-185">När en PSSession är ansluten till den aktuella sessionen **öppnas** dess tillstånd och dess tillgänglighet är **tillgänglig**.</span><span class="sxs-lookup"><span data-stu-id="6333a-185">When a PSSession is connected to the current session, its state is **Opened** and its availability is **Available**.</span></span> <span data-ttu-id="6333a-186">När du kopplar från PSSession är PSSession-läget **frånkopplat** och dess tillgänglighet är **ingen**.</span><span class="sxs-lookup"><span data-stu-id="6333a-186">When you disconnect from the PSSession, the PSSession state is **Disconnected** and its availability is **None**.</span></span>

<span data-ttu-id="6333a-187">Värdet för egenskapen **State** är i förhållande till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-187">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="6333a-188">Värdet **frånkopplat** innebär att PSSession inte är ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-188">A value of **Disconnected** means that the PSSession isn't connected to the current session.</span></span> <span data-ttu-id="6333a-189">Men det betyder inte att PSSession är frånkopplad från alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="6333a-189">But, it doesn't mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="6333a-190">Den kan vara ansluten till en annan session.</span><span class="sxs-lookup"><span data-stu-id="6333a-190">It might be connected to a different session.</span></span>

<span data-ttu-id="6333a-191">Använd egenskapen **Availability** för att avgöra om du kan ansluta eller återansluta till PSSession.</span><span class="sxs-lookup"><span data-stu-id="6333a-191">To determine whether you can connect or reconnect to the PSSession, use the **Availability** property.</span></span> <span data-ttu-id="6333a-192">Värdet **none** anger att du kan ansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-192">A value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="6333a-193">Värdet **upptagen** anger att du inte kan ansluta till PSSession eftersom det är anslutet till en annan session.</span><span class="sxs-lookup"><span data-stu-id="6333a-193">A value of **Busy** indicates that you can't connect to the PSSession because it's connected to another session.</span></span>

<span data-ttu-id="6333a-194">Följande exempel körs i två PowerShell-sessioner på samma dator.</span><span class="sxs-lookup"><span data-stu-id="6333a-194">The following example is run in two PowerShell sessions on the same computer.</span></span>
<span data-ttu-id="6333a-195">Observera de ändrade värdena för egenskaperna **State** och **Availability** i varje session när PSSession är frånkopplad och Återansluten.</span><span class="sxs-lookup"><span data-stu-id="6333a-195">Note the changing values of the **State** and **Availability** properties in each session as the PSSession is disconnected and reconnected.</span></span>

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

<span data-ttu-id="6333a-196">Frånkopplade sessioner underhålls på fjärrdatorn tills du tar bort dem, till exempel med hjälp av `Remove-PSSession` cmdleten eller tids gränsen. Egenskapen **idleTimeout** för en PSSession bestämmer hur länge en frånkopplad session upprätthålls innan den tas bort.</span><span class="sxs-lookup"><span data-stu-id="6333a-196">Disconnected sessions are maintained on the remote computer until you delete them, such as by using the `Remove-PSSession` cmdlet, or they time out. The **IdleTimeout** property of a PSSession determines how long a disconnected session is maintained before it's deleted.</span></span>

<span data-ttu-id="6333a-197">PSSessions är inaktiva när **pulsslags tråden** inte får något svar.</span><span class="sxs-lookup"><span data-stu-id="6333a-197">PSSessions are idle when the **heartbeat thread** receives no response.</span></span>
<span data-ttu-id="6333a-198">Om du kopplar från en session blir den inaktiv och startar **idleTimeout** , även om kommandon fortfarande körs i den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-198">Disconnecting a session makes it idle and starts the **IdleTimeout** clock, even if commands are still running in the disconnected session.</span></span> <span data-ttu-id="6333a-199">I PowerShell anses frånkopplade sessioner vara aktiva, men inaktiva.</span><span class="sxs-lookup"><span data-stu-id="6333a-199">PowerShell considers disconnected sessions to be active, but idle.</span></span>

<span data-ttu-id="6333a-200">När du skapar och kopplar från sessioner kontrollerar du att tids gränsen för inaktivitet i PSSession är tillräckligt lång för att underhålla sessionen för dina behov, men inte så länge den förbrukar onödiga resurser på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-200">When creating and disconnecting sessions, verify that the idle timeout in the PSSession is long enough to maintain the session for your needs, but not so long that it consumes unnecessary resources on the remote computer.</span></span>

<span data-ttu-id="6333a-201">**IdleTimeoutMs** -egenskapen för sessionens konfiguration bestämmer tids gränsen för inaktivitet för sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-201">The **IdleTimeoutMs** property of the session configuration determines the default idle timeout of sessions that use the session configuration.</span></span> <span data-ttu-id="6333a-202">Du kan åsidosätta standardvärdet, men det värde som du använder får inte överskrida **MaxIdleTimeoutMs** -egenskapen för sessionens konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6333a-202">You can override the default value, but the value that you use can't exceed the **MaxIdleTimeoutMs** property of the session configuration.</span></span>

<span data-ttu-id="6333a-203">Använd följande kommando format för att hitta värdet för **IdleTimeoutMs** -och **MaxIdleTimeoutMs** -värden för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-203">To find the value of the **IdleTimeoutMs** and **MaxIdleTimeoutMs** values of a session configuration, use the following command format.</span></span>

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

<span data-ttu-id="6333a-204">Du kan åsidosätta standardvärdet i konfigurationen av sessionen och ange tids gränsen för inaktivitet för en PSSession när du skapar en PSSession och när du kopplar från.</span><span class="sxs-lookup"><span data-stu-id="6333a-204">You can override the default value in the session configuration and set the idle timeout of a PSSession when you create a PSSession and when you disconnect.</span></span>

<span data-ttu-id="6333a-205">Om du är medlem i gruppen Administratörer på fjärrdatorn kan du skapa och ändra egenskaperna **IdleTimeoutMs** och **MaxIdleTimeoutMs** för sessionsinställningar.</span><span class="sxs-lookup"><span data-stu-id="6333a-205">If you're a member of the Administrators group on the remote computer, you can create and change the **IdleTimeoutMs** and **MaxIdleTimeoutMs** properties of session configurations.</span></span>

## <a name="idle-timeout-values"></a><span data-ttu-id="6333a-206">Timeout-värden för inaktivitet</span><span class="sxs-lookup"><span data-stu-id="6333a-206">Idle timeout values</span></span>

<span data-ttu-id="6333a-207">Timeout-värdet för inaktivitet för sessionsinställningar och sessionsinformation är i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="6333a-207">The idle timeout value of session configurations and session options is in milliseconds.</span></span> <span data-ttu-id="6333a-208">Timeout-värdet för inaktivitet i sessioner och konfigurations alternativ för sessioner är i sekunder.</span><span class="sxs-lookup"><span data-stu-id="6333a-208">The idle timeout value of sessions and session configuration options is in seconds.</span></span>

<span data-ttu-id="6333a-209">Du kan ange tids gränsen för inaktivitet för en PSSession när du skapar PSSession ( `New-PSSession` , `Invoke-Command` ) och när du kopplar från den ( `Disconnect-PSSession` ).</span><span class="sxs-lookup"><span data-stu-id="6333a-209">You can set the idle timeout of a PSSession when you create the PSSession (`New-PSSession`, `Invoke-Command`) and when you disconnect from it (`Disconnect-PSSession`).</span></span> <span data-ttu-id="6333a-210">Du kan dock inte ändra **idleTimeout** -värdet när du ansluter till PSSession ( `Connect-PSSession` ) eller hämta resultat ( `Receive-PSSession` ).</span><span class="sxs-lookup"><span data-stu-id="6333a-210">However, you can't change the **IdleTimeout** value when you connect to the PSSession (`Connect-PSSession`) or get results (`Receive-PSSession`).</span></span>

<span data-ttu-id="6333a-211">`Connect-PSSession` `Receive-PSSession` Cmdletarna och har en **SessionOption** -parameter som tar ett **SessionOption** -objekt, till exempel en som returneras av `New-PSSessionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6333a-211">The `Connect-PSSession` and `Receive-PSSession` cmdlets have a **SessionOption** parameter that takes a **SessionOption** object, such as one returned by the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="6333a-212">**IdleTimeout** -värdet i **SessionOption** -objektet och **idleTimeout** -värdet i `$PSSessionOption` variabeln Preference ändrar inte värdet för **idleTimeout** för PSSession i ett- `Connect-PSSession` eller- `Receive-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="6333a-212">The **IdleTimeout** value in **SessionOption** object and the **IdleTimeout** value in the `$PSSessionOption` preference variable don't change the value of the **IdleTimeout** of the PSSession in a `Connect-PSSession` or `Receive-PSSession` command.</span></span>

<span data-ttu-id="6333a-213">Skapa en inställnings variabel om du vill skapa en PSSession med ett visst tids gräns värde för inaktivitet `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="6333a-213">To create a PSSession with a particular idle timeout value, create a `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="6333a-214">Ange värdet för **idleTimeout** -egenskapen till önskat värde (i millisekunder).</span><span class="sxs-lookup"><span data-stu-id="6333a-214">Set the value of the **IdleTimeout** property to the desired value (in milliseconds).</span></span>

<span data-ttu-id="6333a-215">När du skapar PSSessions prioriteras värdena i `$PSSessionOption` variabeln över värdena i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-215">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="6333a-216">Följande kommando anger till exempel en timeout för inaktivitet på 48 timmar:</span><span class="sxs-lookup"><span data-stu-id="6333a-216">For example, the following command sets an idle timeout of 48 hours:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

<span data-ttu-id="6333a-217">Om du vill skapa en PSSession med ett visst tids gräns värde för inaktivitet, använder du parametern **IdleTimeoutMSec** för `New-PSSessionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6333a-217">To create a PSSession with a particular idle timeout value, use the **IdleTimeoutMSec** parameter of the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="6333a-218">Använd sedan alternativet session i värdet för parametern **SessionOption** i `New-PSSession` `Invoke-Command` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="6333a-218">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="6333a-219">Värdena som anges när du skapar sessionen prioriteras framför de värden som anges i `$PSSessionOption` variabeln Preference och konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-219">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="6333a-220">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-220">For example:</span></span>

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

<span data-ttu-id="6333a-221">Om du vill ändra tids gränsen för inaktivitet för en PSSession vid från koppling använder du parametern **IdleTimeoutSec** för `Disconnect-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6333a-221">To change the idle timeout of a PSSession when disconnecting, use the **IdleTimeoutSec** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="6333a-222">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-222">For example:</span></span>

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

<span data-ttu-id="6333a-223">Om du vill skapa en sessionshantering med en viss tids gräns för inaktivitet och maximal tids gräns för inaktivitet använder du cmdleten **IdleTimeoutSec** och **MaxIdleTimeoutSec** `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="6333a-223">To create a session configuration with a particular idle timeout and maximum idle timeout, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="6333a-224">Använd sedan alternativet transport i värdet för parametern **TransportOption** i `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6333a-224">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="6333a-225">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-225">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="6333a-226">Om du vill ändra standard tids gränsen för inaktivitet och maximal tids gräns för inaktivitet för en session, använder du cmdleten **IdleTimeoutSec** och **MaxIdleTimeoutSec** `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="6333a-226">To change the default idle timeout and maximum idle timeout of a session configuration, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="6333a-227">Använd sedan alternativet transport i värdet för parametern **TransportOption** i `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6333a-227">Then, use the transport option in the value of the **TransportOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="6333a-228">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-228">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a><span data-ttu-id="6333a-229">Läge för buffring av utdata</span><span class="sxs-lookup"><span data-stu-id="6333a-229">Output buffering mode</span></span>

<span data-ttu-id="6333a-230">Utmatnings buffertens läge för en PSSession bestämmer hur kommandoutdata hanteras när utdatabufferten för PSSession är full.</span><span class="sxs-lookup"><span data-stu-id="6333a-230">The output buffering mode of a PSSession determines how command output is managed when the output buffer of the PSSession is full.</span></span>

<span data-ttu-id="6333a-231">I en frånkopplad session avgör utmatnings buffertens läge om kommandot fortsätter att köras medan sessionen kopplas från.</span><span class="sxs-lookup"><span data-stu-id="6333a-231">In a disconnected session, the output buffering mode effectively determines whether the command continues to run while the session is disconnected.</span></span>

<span data-ttu-id="6333a-232">Giltiga värden enligt följande:</span><span class="sxs-lookup"><span data-stu-id="6333a-232">The valid values as follows:</span></span>

- <span data-ttu-id="6333a-233">**Blockera**.</span><span class="sxs-lookup"><span data-stu-id="6333a-233">**Block**.</span></span> <span data-ttu-id="6333a-234">När utdatabufferten är full pausas körningen tills bufferten är klar.</span><span class="sxs-lookup"><span data-stu-id="6333a-234">When the output buffer is full, execution is suspended until the buffer is clear.</span></span> <span data-ttu-id="6333a-235">Standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="6333a-235">The default value.</span></span>
- <span data-ttu-id="6333a-236">**Släpp**.</span><span class="sxs-lookup"><span data-stu-id="6333a-236">**Drop**.</span></span> <span data-ttu-id="6333a-237">När utdatabufferten är full fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="6333a-237">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="6333a-238">När nya utdata skapas, ignoreras det äldsta resultatet.</span><span class="sxs-lookup"><span data-stu-id="6333a-238">As new output is generated, the oldest output is discarded.</span></span>

<span data-ttu-id="6333a-239">**Blockera** data bevarar data, men kan avbryta kommandot.</span><span class="sxs-lookup"><span data-stu-id="6333a-239">**Block** preserves data, but might interrupt the command.</span></span> <span data-ttu-id="6333a-240">Ett **Drop** -värde gör att kommandot kan slutföras, men data kan gå förlorade.</span><span class="sxs-lookup"><span data-stu-id="6333a-240">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="6333a-241">När du använder **Drop** -värdet dirigerar du om kommandots utdata till en fil på disk.</span><span class="sxs-lookup"><span data-stu-id="6333a-241">When using the **Drop** value, redirect the command output to a file on disk.</span></span> <span data-ttu-id="6333a-242">Det här värdet rekommenderas för frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="6333a-242">This value is recommended for disconnected sessions.</span></span>

<span data-ttu-id="6333a-243">**OutputBufferingMode** -egenskapen för sessionens konfiguration bestämmer standardutdata för buffring av sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-243">The **OutputBufferingMode** property of the session configuration determines the default output buffering mode of sessions that use the session configuration.</span></span>

<span data-ttu-id="6333a-244">Om du vill hitta en konfigurations värde för en **OutputBufferingMode** kan du använda något av följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="6333a-244">To find a session configuration's value of the **OutputBufferingMode**, you can use either of the following command formats:</span></span>

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

<span data-ttu-id="6333a-245">Du kan åsidosätta standardvärdet i konfigurationen av sessionen och ange ett PSSession när du skapar en PSSession när du kopplar från, och när du återansluter.</span><span class="sxs-lookup"><span data-stu-id="6333a-245">You can override the default value in the session configuration and set the output buffering mode of a PSSession when you create a PSSession, when you disconnect, and when you reconnect.</span></span>

<span data-ttu-id="6333a-246">Om du är medlem i gruppen Administratörer på fjärrdatorn kan du skapa och ändra buffrings läget för utdata i sessioner.</span><span class="sxs-lookup"><span data-stu-id="6333a-246">If you're a member of the Administrators group on the remote computer, you can create and change the output buffering mode of session configurations.</span></span>

<span data-ttu-id="6333a-247">Om du vill skapa en PSSession med ett utmatnings **Buffer-läge**, skapar du en `$PSSessionOption` Preference-variabel där värdet för egenskapen **OutputBufferingMode** är **Drop**.</span><span class="sxs-lookup"><span data-stu-id="6333a-247">To create a PSSession with an output buffering mode of **Drop**, create a `$PSSessionOption` preference variable in which the value of the **OutputBufferingMode** property is **Drop**.</span></span>

<span data-ttu-id="6333a-248">När du skapar PSSessions prioriteras värdena i `$PSSessionOption` variabeln över värdena i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-248">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="6333a-249">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-249">For example:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

<span data-ttu-id="6333a-250">Om du vill skapa en PSSession med ett utmatnings **Buffer-läge**, använder du parametern **OutputBufferingMode** för cmdlet: en för `New-PSSessionOption` att skapa ett session-alternativ med värdet **Drop**.</span><span class="sxs-lookup"><span data-stu-id="6333a-250">To create a PSSession with an output buffering mode of **Drop**, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="6333a-251">Använd sedan alternativet session i värdet för parametern **SessionOption** i `New-PSSession` `Invoke-Command` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="6333a-251">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="6333a-252">Värdena som anges när du skapar sessionen prioriteras framför de värden som anges i `$PSSessionOption` variabeln Preference och konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6333a-252">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="6333a-253">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-253">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

<span data-ttu-id="6333a-254">Om du vill ändra utdata buffer-läget för en PSSession vid från koppling använder du parametern **OutputBufferingMode** för `Disconnect-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6333a-254">To change the output buffering mode of a PSSession when disconnecting, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="6333a-255">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-255">For example:</span></span>

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

<span data-ttu-id="6333a-256">Om du vill ändra utdata buffer-läget för en PSSession vid åter anslutning använder du parametern **OutputBufferingMode** för cmdlet: en `New-PSSessionOption` för att skapa ett session-alternativ med värdet **Drop**.</span><span class="sxs-lookup"><span data-stu-id="6333a-256">To change the output buffering mode of a PSSession when reconnecting, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop**.</span></span> <span data-ttu-id="6333a-257">Använd sedan alternativet session i värdet för parametern **SessionOption** i `Connect-PSSession` eller `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6333a-257">Then, use the session option in the value of the **SessionOption** parameter of `Connect-PSSession` or `Receive-PSSession`.</span></span>

<span data-ttu-id="6333a-258">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-258">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

<span data-ttu-id="6333a-259">Om du vill skapa en konfiguration av sessionen med ett utmatnings sätt **som är** förvalt, använder du parametern **OutputBufferingMode** för `New-PSTransportOption` cmdleten för att skapa ett transport alternativ objekt med värdet **Drop**.</span><span class="sxs-lookup"><span data-stu-id="6333a-259">To create a session configuration with a default output buffering mode of **Drop**, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option object with a value of **Drop**.</span></span> <span data-ttu-id="6333a-260">Använd sedan alternativet transport i värdet för parametern **TransportOption** i `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6333a-260">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="6333a-261">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-261">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="6333a-262">Om du vill ändra standard läget för buffring av utdata för en session, använder du parametern **OutputBufferingMode** för `New-PSTransportOption` cmdlet: en för att skapa ett transport alternativ med värdet **Drop**.</span><span class="sxs-lookup"><span data-stu-id="6333a-262">To change the default output buffering mode of a session configuration, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option with a value of **Drop**.</span></span> <span data-ttu-id="6333a-263">Använd sedan alternativet transport i värdet för parametern **SessionOption** i `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6333a-263">Then, use the Transport option in the value of the **SessionOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="6333a-264">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6333a-264">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a><span data-ttu-id="6333a-265">Koppla från loopback-sessioner</span><span class="sxs-lookup"><span data-stu-id="6333a-265">Disconnecting loopback sessions</span></span>

<span data-ttu-id="6333a-266">Loopback-sessioner, eller lokala sessioner, är PSSessions som kommer från och slutar på samma dator.</span><span class="sxs-lookup"><span data-stu-id="6333a-266">Loopback sessions, or local sessions, are PSSessions that originate and terminate on the same computer.</span></span> <span data-ttu-id="6333a-267">Precis som andra PSSessions underhålls aktiva loopback-sessioner på datorn i Fjärrslutpunkten av anslutningen (den lokala datorn) så att du kan koppla från och återansluta till loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="6333a-267">Like other PSSessions, active loopback sessions are maintained on the computer on the remote end of the connection (the local computer), so you can disconnect from and reconnect to loopback sessions.</span></span>

<span data-ttu-id="6333a-268">Som standard skapas loopback-sessioner med en nätverks säkerhets-token som inte tillåter att kommandon körs i sessionen för att få åtkomst till andra datorer.</span><span class="sxs-lookup"><span data-stu-id="6333a-268">By default, loopback sessions are created with a network security token that doesn't permit commands run in the session to access other computers.</span></span> <span data-ttu-id="6333a-269">Du kan återansluta till loopback-sessioner som har en nätverks säkerhets-token från valfri session på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="6333a-269">You can reconnect to loopback sessions that have a network security token from any session on the local computer or a remote computer.</span></span>

<span data-ttu-id="6333a-270">Men om du använder parametern **EnableNetworkAccess** i `New-PSSession` `Enter-PSSession` cmdleten, eller, `Invoke-Command` skapas loopback-sessionen med en interaktiv säkerhetstoken.</span><span class="sxs-lookup"><span data-stu-id="6333a-270">However, if you use the **EnableNetworkAccess** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlet, the loopback session is created with an interactive security token.</span></span> <span data-ttu-id="6333a-271">Den interaktiva token gör det möjligt att köra kommandon som körs i loopback-sessionen för att hämta data från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="6333a-271">The interactive token enables commands that run in the loopback session to get data from other computers.</span></span>

<span data-ttu-id="6333a-272">Du kan koppla från loopback-sessioner med interaktiva token och sedan återansluta till dem från samma session eller en annan session på samma dator.</span><span class="sxs-lookup"><span data-stu-id="6333a-272">You can disconnect loopback sessions with interactive tokens and then reconnect to them from the same session or a different session on the same computer.</span></span>
<span data-ttu-id="6333a-273">Men för att förhindra obehörig åtkomst kan du återansluta till loopback-sessioner med interaktiva tokens enbart från den dator där de skapades.</span><span class="sxs-lookup"><span data-stu-id="6333a-273">However, to prevent malicious access, you can reconnect to loopback sessions with interactive tokens only from the computer on which they were created.</span></span>

## <a name="waiting-for-jobs-in-disconnected-sessions"></a><span data-ttu-id="6333a-274">Väntar på jobb i frånkopplade sessioner</span><span class="sxs-lookup"><span data-stu-id="6333a-274">Waiting for jobs in disconnected sessions</span></span>

<span data-ttu-id="6333a-275">`Wait-Job`Cmdleten väntar tills ett jobb har slutförts och återgår sedan till kommando tolken eller nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="6333a-275">The `Wait-Job` cmdlet waits until a job completes and then returns to the command prompt or the next command.</span></span> <span data-ttu-id="6333a-276">Som standard `Wait-Job` returneras om sessionen där ett jobb körs är frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="6333a-276">By default, `Wait-Job` returns if the session in which a job is running is disconnected.</span></span> <span data-ttu-id="6333a-277">Om du vill dirigera `Wait-Job` cmdleten till att vänta tills sessionen har återanslutits använder du parametern **Force** i **öppnings** läge.</span><span class="sxs-lookup"><span data-stu-id="6333a-277">To direct the `Wait-Job` cmdlet to wait until the session is reconnected, in the **Opened** state, use the **Force** parameter.</span></span> <span data-ttu-id="6333a-278">Mer information finns i [wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span><span class="sxs-lookup"><span data-stu-id="6333a-278">For more information, see [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span></span>

## <a name="robust-sessions-and-unintentional-disconnection"></a><span data-ttu-id="6333a-279">Robusta sessioner och oavsiktlig från koppling</span><span class="sxs-lookup"><span data-stu-id="6333a-279">Robust sessions and unintentional disconnection</span></span>

<span data-ttu-id="6333a-280">En PSSession kan oavsiktligt kopplas från på grund av ett dator haveri eller nätverks avbrott.</span><span class="sxs-lookup"><span data-stu-id="6333a-280">A PSSession might be unintentionally disconnected because of a computer failure or network outage.</span></span> <span data-ttu-id="6333a-281">PowerShell försöker återställa PSSession, men dess framgång beror på orsakens allvarlighets grad och varaktighet.</span><span class="sxs-lookup"><span data-stu-id="6333a-281">PowerShell attempts to recover the PSSession, but its success depends upon the severity and duration of the cause.</span></span>

<span data-ttu-id="6333a-282">Statusen för en oavsiktligt frånkopplad PSSession kan vara **bruten** eller **stängd**, men den kan också vara **frånkopplad**.</span><span class="sxs-lookup"><span data-stu-id="6333a-282">The state of an unintentionally disconnected PSSession might be **Broken** or **Closed**, but it might also be **Disconnected**.</span></span> <span data-ttu-id="6333a-283">Om värdet för **State** är **frånkopplat** kan du använda samma metoder för att hantera PSSession på samma sätt som om sessionen kopplades från avsiktligt.</span><span class="sxs-lookup"><span data-stu-id="6333a-283">If the value of **State** is **Disconnected**, you can use the same techniques to manage the PSSession as you would if the session were disconnected intentionally.</span></span> <span data-ttu-id="6333a-284">Du kan till exempel använda `Connect-PSSession` cmdleten för att återansluta till sessionen och `Receive-PSSession` cmdleten för att få resultat från kommandon som kördes medan sessionen kopplades från.</span><span class="sxs-lookup"><span data-stu-id="6333a-284">For example, you can use the `Connect-PSSession` cmdlet to reconnect to the session and the `Receive-PSSession` cmdlet to get results of commands that ran while the session was disconnected.</span></span>

<span data-ttu-id="6333a-285">Om du stänger (avslutar) sessionen där en PSSession skapades medan kommandon körs i PSSession, underhåller PowerShell PSSession i **frånkopplat** läge på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="6333a-285">If you close (exit) the session in which a PSSession was created while commands are running in the PSSession, PowerShell maintains the PSSession in the **Disconnected** state on the remote computer.</span></span> <span data-ttu-id="6333a-286">Om du stänger (avslutar) sessionen där en PSSession skapades men inga kommandon körs i PSSession, försöker inte PowerShell underhålla PSSession.</span><span class="sxs-lookup"><span data-stu-id="6333a-286">If you close (exit) the session in which a PSSession was created, but no commands are running in the PSSession, PowerShell doesn't attempt to maintain the PSSession.</span></span>

## <a name="see-also"></a><span data-ttu-id="6333a-287">Se även</span><span class="sxs-lookup"><span data-stu-id="6333a-287">See also</span></span>

[<span data-ttu-id="6333a-288">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="6333a-288">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="6333a-289">about_Remote</span><span class="sxs-lookup"><span data-stu-id="6333a-289">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="6333a-290">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="6333a-290">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="6333a-291">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="6333a-291">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="6333a-292">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="6333a-292">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="6333a-293">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="6333a-293">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="6333a-294">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="6333a-294">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="6333a-295">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="6333a-295">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="6333a-296">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="6333a-296">Receive-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[<span data-ttu-id="6333a-297">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="6333a-297">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

