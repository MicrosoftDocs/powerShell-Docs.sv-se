---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Använda Windows PowerShell 2,0-motorn
ms.openlocfilehash: c5ac92159d63e5669643908016186ed32dfb46db
ms.sourcegitcommit: 3e343f005fe76960c998ef1869a1a093d37ef349
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216030"
---
# <a name="using-the-windows-powershell-20-engine"></a><span data-ttu-id="e6d36-103">Använda Windows PowerShell 2,0-motorn</span><span class="sxs-lookup"><span data-stu-id="e6d36-103">Using the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="e6d36-104">Windows PowerShell är utformat för att vara bakåtkompatibelt med tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="e6d36-104">Windows PowerShell is designed to be backward compatible with previous versions.</span></span> <span data-ttu-id="e6d36-105">Cmdlets, providers, snapin-moduler, moduler och skript som skrivits för Windows PowerShell 2,0 körs oförändrade i nyare versioner av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6d36-105">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in newer versions Windows PowerShell.</span></span> <span data-ttu-id="e6d36-106">Microsoft .NET Framework 4 ändrade dock aktiverings principen för körning.</span><span class="sxs-lookup"><span data-stu-id="e6d36-106">However, Microsoft .NET Framework 4 changed the runtime activation policy.</span></span>
<span data-ttu-id="e6d36-107">Windows PowerShell-värdprogram som skrivits för Windows PowerShell 2,0 och kompileras med CLR (Common Language Runtime) 2,0 kan inte köras utan ändringar i nya versioner Windows PowerShell som kompileras med CLR 4,0 (eller högre).</span><span class="sxs-lookup"><span data-stu-id="e6d36-107">Windows PowerShell host programs written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in new versions Windows PowerShell that are compiled with CLR 4.0 (or higher).</span></span>

<span data-ttu-id="e6d36-108">Windows PowerShell 2,0-motorn är avsedd att användas endast när ett befintligt skript eller värd program inte kan köras eftersom det är inkompatibelt med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="e6d36-108">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 5.1.</span></span> <span data-ttu-id="e6d36-109">Exempel på detta är äldre versioner av Exchange eller SQL Server moduler.</span><span class="sxs-lookup"><span data-stu-id="e6d36-109">Examples of this include older versions of Exchange or SQL Server modules.</span></span> <span data-ttu-id="e6d36-110">Sådana fall förväntas vara ovanliga.</span><span class="sxs-lookup"><span data-stu-id="e6d36-110">Such cases are expected to be rare.</span></span>

<span data-ttu-id="e6d36-111">Många program som kräver Windows PowerShell 2,0-motorn startar automatiskt.</span><span class="sxs-lookup"><span data-stu-id="e6d36-111">Many programs that require the Windows PowerShell 2.0 Engine start it automatically.</span></span> <span data-ttu-id="e6d36-112">Dessa instruktioner ingår i de sällsynta situationer där du måste starta motorn manuellt.</span><span class="sxs-lookup"><span data-stu-id="e6d36-112">These instructions are included for the rare situations in which you need to start the engine manually.</span></span>

## <a name="deprecation-and-security-concerns"></a><span data-ttu-id="e6d36-113">Utfasnings-och säkerhets problem</span><span class="sxs-lookup"><span data-stu-id="e6d36-113">Deprecation and security concerns</span></span>

<span data-ttu-id="e6d36-114">Windows PowerShell 2,0 föråldrades i augusti 2017.</span><span class="sxs-lookup"><span data-stu-id="e6d36-114">Windows PowerShell 2.0 was deprecated in August, 2017.</span></span> <span data-ttu-id="e6d36-115">Mer information finns i [meddelandet][] på PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="e6d36-115">For more information, see the [announcement][] on the PowerShell blog.</span></span>

<span data-ttu-id="e6d36-116">Windows PowerShell 2,0 saknar en betydande mängd härdnings-och säkerhetsfunktioner som har lagts till i version 3, 4 och 5.</span><span class="sxs-lookup"><span data-stu-id="e6d36-116">Windows PowerShell 2.0 is missing a significant amount of the hardening and security features added in versions 3, 4, and 5.</span></span> <span data-ttu-id="e6d36-117">Vi rekommenderar starkt att användarna inte använder den om de kan hjälpa dem.</span><span class="sxs-lookup"><span data-stu-id="e6d36-117">We highly, highly recommend that users not use it if they can help it.</span></span> <span data-ttu-id="e6d36-118">Mer information finns i [jämförelse av gränssnitts-och skript språk säkerhet][] och [PowerShell ♥ blått-teamet][blueteam].</span><span class="sxs-lookup"><span data-stu-id="e6d36-118">For more information, see [A Comparison of Shell and Scripting Language Security][] and [PowerShell ♥ the Blue Team][blueteam].</span></span>

## <a name="installing-and-enabling-required-programs"></a><span data-ttu-id="e6d36-119">Installera och aktivera nödvändiga program</span><span class="sxs-lookup"><span data-stu-id="e6d36-119">Installing and Enabling Required Programs</span></span>

<span data-ttu-id="e6d36-120">Innan du startar Windows PowerShell 2,0-motorn aktiverar du Windows PowerShell 2,0-motorn och Microsoft .NET Framework 3,5 med Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="e6d36-120">Before starting the Windows PowerShell 2.0 Engine, enable the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 with Service Pack 1.</span></span> <span data-ttu-id="e6d36-121">Instruktioner finns i [Installera Windows PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="e6d36-121">For instructions, see [Installing Windows PowerShell][].</span></span>

<span data-ttu-id="e6d36-122">System där Windows Management Framework 3,0 eller senare har installerats har alla nödvändiga komponenter.</span><span class="sxs-lookup"><span data-stu-id="e6d36-122">Systems on which Windows Management Framework 3.0 or higher is installed have all of the required components.</span></span> <span data-ttu-id="e6d36-123">Ingen ytterligare konfiguration krävs.</span><span class="sxs-lookup"><span data-stu-id="e6d36-123">No further configuration is necessary.</span></span> <span data-ttu-id="e6d36-124">Information om hur du installerar Windows Management Framework finns i [Installera och konfigurera WMF][].</span><span class="sxs-lookup"><span data-stu-id="e6d36-124">For information about installing Windows Management Framework, see [Install and configure WMF][].</span></span>

## <a name="how-to-start-the-windows-powershell-20-engine"></a><span data-ttu-id="e6d36-125">Starta Windows PowerShell 2,0-motorn</span><span class="sxs-lookup"><span data-stu-id="e6d36-125">How to start the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="e6d36-126">När du startar Windows PowerShell startas den senaste versionen som standard.</span><span class="sxs-lookup"><span data-stu-id="e6d36-126">When you start Windows PowerShell the newest version starts by default.</span></span> <span data-ttu-id="e6d36-127">Starta Windows PowerShell med Windows PowerShell 2,0-motorn med hjälp av parametern version i `PowerShell.exe` .</span><span class="sxs-lookup"><span data-stu-id="e6d36-127">To start Windows PowerShell with the Windows PowerShell 2.0 Engine, use the Version parameter of `PowerShell.exe`.</span></span> <span data-ttu-id="e6d36-128">Du kan köra kommandot i valfri kommando tolk, inklusive Windows PowerShell och Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="e6d36-128">You can run the command at any command prompt, including Windows PowerShell and Cmd.exe.</span></span>

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a><span data-ttu-id="e6d36-129">Så här startar du en fjärrsession med Windows PowerShell 2,0-motorn</span><span class="sxs-lookup"><span data-stu-id="e6d36-129">How to start a remote session with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="e6d36-130">Om du vill köra Windows PowerShell 2,0-motorn i en fjärran sluten session skapar du en sessionsnyckel (kallas även _slut punkt_) på den fjärrdator som läser in Windows PowerShell 2,0-motorn.</span><span class="sxs-lookup"><span data-stu-id="e6d36-130">To run the Windows PowerShell 2.0 Engine in a remote session, create a session configuration (also known as an _endpoint_) on the remote computer that loads the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="e6d36-131">Konfigurationen av sessionen sparas på fjärrdatorn och kan användas av alla auktoriserade användare för att skapa sessioner som använder Windows PowerShell 2,0-motorn.</span><span class="sxs-lookup"><span data-stu-id="e6d36-131">The session configuration is saved on the remote computer and can be used by any authorized user to create sessions that use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="e6d36-132">Detta är en avancerad uppgift som vanligt vis utförs av en system administratör.</span><span class="sxs-lookup"><span data-stu-id="e6d36-132">This is an advanced task that is typically performed by a system administrator.</span></span>

<span data-ttu-id="e6d36-133">I följande procedur används parametern **PSVersion** i cmdleten [register-PSSessionConfiguration][] för att skapa en sessionsnyckel som använder Windows PowerShell 2,0-motorn.</span><span class="sxs-lookup"><span data-stu-id="e6d36-133">The following procedure uses the **PSVersion** parameter of the [Register-PSSessionConfiguration][] cmdlet to create a session configuration that uses the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="e6d36-134">Du kan också använda parametern **PowerShellVersion** för [New-PSSessionConfigurationFile][] -cmdlet: en för att skapa en konfigurations fil för sessionen för en session som läser in Windows PowerShell 2,0-motorn och du kan använda parametern **PSVersion** för parametern [set-PSSessionConfiguration][] för att ändra en sessions konfiguration till att använda Windows PowerShell 2,0-motorn.</span><span class="sxs-lookup"><span data-stu-id="e6d36-134">You can also use the **PowerShellVersion** parameter of the [New-PSSessionConfigurationFile][] cmdlet to create a session configuration file for a session that loads the Windows PowerShell 2.0 Engine and you can use the **PSVersion** parameter of the [Set-PSSessionConfiguration][] parameter to change a session configuration to use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="e6d36-135">Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files][].</span><span class="sxs-lookup"><span data-stu-id="e6d36-135">For more information about session configuration files, see [about_Session_Configuration_Files][].</span></span>
<span data-ttu-id="e6d36-136">Information om sessionsdata, inklusive konfiguration och säkerhet, finns [about_Session_Configurations][].</span><span class="sxs-lookup"><span data-stu-id="e6d36-136">For information about session configurations, including setup and security, see [about_Session_Configurations][].</span></span>

### <a name="to-start-a-remote-windows-powershell-20-session"></a><span data-ttu-id="e6d36-137">Starta en fjärran sluten Windows PowerShell 2,0-session</span><span class="sxs-lookup"><span data-stu-id="e6d36-137">To start a remote Windows PowerShell 2.0 session</span></span>

1. <span data-ttu-id="e6d36-138">Om du vill skapa en sessionsnyckel som kräver Windows PowerShell 2,0-motorn använder du parametern **PSVersion** för `Register-PSSessionConfiguration` cmdleten med värdet `2.0` .</span><span class="sxs-lookup"><span data-stu-id="e6d36-138">To create a session configuration that requires the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet with a value of `2.0`.</span></span>
   <span data-ttu-id="e6d36-139">Kör det här kommandot på datorn på "Server sidan" eller ta emot slutet av anslutningen.</span><span class="sxs-lookup"><span data-stu-id="e6d36-139">Run this command on the computer at the "server side" or receiving end of the connection.</span></span>

   <span data-ttu-id="e6d36-140">Följande exempel kommando skapar PS2-sessionen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="e6d36-140">The following sample command creates the PS2 session configuration on the Server01 computer.</span></span> <span data-ttu-id="e6d36-141">Starta Windows PowerShell med alternativet **Kör som administratör** för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="e6d36-141">To run this command, start Windows PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. <span data-ttu-id="e6d36-142">Om du vill skapa en session på Server01-datorn som använder PS2-sessionen använder du parametern **ConfigurationName** för cmdlet: ar som skapar en fjärrsession, till exempel cmdleten "New-PSSession".</span><span class="sxs-lookup"><span data-stu-id="e6d36-142">To create a session on the Server01 computer that uses the PS2 session configuration, use the **ConfigurationName** parameter of cmdlets that create a remote session, such as the \`New-PSSession cmdlet.</span></span>

   <span data-ttu-id="e6d36-143">När en session som använder sessionen startar läses Windows PowerShell 2,0-motorn automatiskt in i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e6d36-143">When a session that uses the session configuration starts, the Windows PowerShell 2.0 Engine is automatically loaded into the session.</span></span>

   <span data-ttu-id="e6d36-144">Följande kommando startar en-session på Server01-datorn som använder PS2-sessionen.</span><span class="sxs-lookup"><span data-stu-id="e6d36-144">The following command starts a session on the Server01 computer that uses the PS2 session configuration.</span></span> <span data-ttu-id="e6d36-145">Kommandot sparar sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e6d36-145">The command saves the session in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a><span data-ttu-id="e6d36-146">Så här startar du ett bakgrunds jobb med Windows PowerShell 2,0-motorn</span><span class="sxs-lookup"><span data-stu-id="e6d36-146">How to start a background job with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="e6d36-147">Om du vill starta ett bakgrunds jobb med Windows PowerShell 2,0-motorn använder du parametern **PSVersion** i cmdleten [Start-Job][] .</span><span class="sxs-lookup"><span data-stu-id="e6d36-147">To start a background job with the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Start-Job][] cmdlet.</span></span>

<span data-ttu-id="e6d36-148">Följande kommando startar ett bakgrunds jobb med Windows PowerShell 2,0-motorn</span><span class="sxs-lookup"><span data-stu-id="e6d36-148">The following command starts a background job with the Windows PowerShell 2.0 Engine</span></span>

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

<span data-ttu-id="e6d36-149">Mer information om bakgrunds jobb finns [about_Jobs][].</span><span class="sxs-lookup"><span data-stu-id="e6d36-149">For more information about background jobs, see [about_Jobs][].</span></span>

<!-- link references -->
[känna]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[announcement]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Jämförelse mellan gränssnitts-och skript språk säkerhet]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[A Comparison of Shell and Scripting Language Security]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Installera Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installing Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installera och konfigurera WMF]: wmf/setup/install-configure.md
[Install and configure WMF]: wmf/setup/install-configure.md
[Registrera – PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfigurationFile
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start – jobb]: /powershell/module/microsoft.powershell.core/start-job
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
