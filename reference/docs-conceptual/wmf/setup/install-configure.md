---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
contributor: keithb
title: Installera och konfigurera WMF 5.1
ms.openlocfilehash: 241f52be011e1afc87d25c9a934db0c1e0361b76
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404812"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="3bca5-103">Installera och konfigurera WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="3bca5-103">Install and Configure WMF 5.1</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3bca5-104">WMF 5,0 ersätts av WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="3bca5-104">WMF 5.0 is superseded by WMF 5.1.</span></span> <span data-ttu-id="3bca5-105">Användare med WMF 5,0 måste uppgradera till WMF 5,1 för att få support.</span><span class="sxs-lookup"><span data-stu-id="3bca5-105">Users with WMF 5.0 must upgrade to WMF 5.1 to receive support.</span></span>
> <span data-ttu-id="3bca5-106">**WMF 5,1 kräver .NET Framework 4.5.2** (eller senare).</span><span class="sxs-lookup"><span data-stu-id="3bca5-106">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="3bca5-107">Installationen kommer att lyckas, men viktiga funktioner kommer att Miss lyckas om .NET 4.5.2 (eller senare) inte är installerat.</span><span class="sxs-lookup"><span data-stu-id="3bca5-107">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="3bca5-108">Hämta och installera WMF 5,1-paketet</span><span class="sxs-lookup"><span data-stu-id="3bca5-108">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="3bca5-109">Hämta WMF 5,1-paketet för det operativ system och den arkitektur som du vill installera den på:</span><span class="sxs-lookup"><span data-stu-id="3bca5-109">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="3bca5-110">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="3bca5-110">Operating System</span></span>       | <span data-ttu-id="3bca5-111">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="3bca5-111">Prerequisites</span></span>           | <span data-ttu-id="3bca5-112">Paket länkar</span><span class="sxs-lookup"><span data-stu-id="3bca5-112">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="3bca5-113">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3bca5-113">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="3bca5-114">[Win 8.1 AndW2K12R2-KB3191564-x64. msu][]</span><span class="sxs-lookup"><span data-stu-id="3bca5-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="3bca5-115">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3bca5-115">Windows Server 2012</span></span>    |                         | <span data-ttu-id="3bca5-116">[W2K12-KB3191565-x64. msu][]</span><span class="sxs-lookup"><span data-stu-id="3bca5-116">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="3bca5-117">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="3bca5-117">Windows Server 2008 R2</span></span> | <span data-ttu-id="3bca5-118">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="3bca5-118">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="3bca5-119">[Win7AndW2K8R2-KB3191566-x64. ZIP][]</span><span class="sxs-lookup"><span data-stu-id="3bca5-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="3bca5-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="3bca5-120">Windows 8.1</span></span>            |                         | <span data-ttu-id="3bca5-121">**x64:** [Win 8.1 andw2k12r2-kb3191564-x64. msu][]</span><span class="sxs-lookup"><span data-stu-id="3bca5-121">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="3bca5-122">**x86:** [Win 8.1-kb3191564-x86. msu][]</span><span class="sxs-lookup"><span data-stu-id="3bca5-122">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="3bca5-123">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3bca5-123">Windows 7 SP1</span></span>          | <span data-ttu-id="3bca5-124">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="3bca5-124">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="3bca5-125">**x64:** [Win7AndW2K8R2-KB3191566-x64. zip][]</span><span class="sxs-lookup"><span data-stu-id="3bca5-125">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="3bca5-126">**x86:** [Win7-KB3191566-x86. zip][]</span><span class="sxs-lookup"><span data-stu-id="3bca5-126">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64. msu]: https://go.microsoft.com/fwlink/?linkid=839513
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86. ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64. ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win 8.1-KB3191564-x86. msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win 8.1 AndW2K12R2-KB3191564-x64. msu]: https://go.microsoft.com/fwlink/?linkid=839516
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- <span data-ttu-id="3bca5-133">WMF 5,1 Preview måste avinstalleras innan du installerar WMF 5,1 RTM.</span><span class="sxs-lookup"><span data-stu-id="3bca5-133">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="3bca5-134">WMF 5,1 kan installeras direkt över WMF 5,0 eller WMF 4,0.</span><span class="sxs-lookup"><span data-stu-id="3bca5-134">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="3bca5-135">Du **behöver inte** installera WMF 4,0 innan du installerar WMF 5,1 på Windows 7 och windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="3bca5-135">It is **not required** to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="3bca5-136">Installera WMF 5,1 för Windows Server 2008 R2 och Windows 7</span><span class="sxs-lookup"><span data-stu-id="3bca5-136">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> [!NOTE]
> <span data-ttu-id="3bca5-137">Installations anvisningar för Windows Server 2008 R2 och Windows 7 har ändrats och skiljer sig från anvisningarna för de andra paketen.</span><span class="sxs-lookup"><span data-stu-id="3bca5-137">Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="3bca5-138">Installations anvisningar för Windows Server 2012 R2, Windows Server 2012 och Windows 8,1 finns nedan.</span><span class="sxs-lookup"><span data-stu-id="3bca5-138">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a><span data-ttu-id="3bca5-139">WMF 5,1-krav för Windows Server 2008 R2 SP1 och Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3bca5-139">WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1</span></span>

<span data-ttu-id="3bca5-140">Installationen av WMF 5,1 på antingen Windows Server 2008 R2 SP1 eller Windows 7 SP1 kräver följande:</span><span class="sxs-lookup"><span data-stu-id="3bca5-140">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>

- <span data-ttu-id="3bca5-141">Senaste service pack måste vara installerat.</span><span class="sxs-lookup"><span data-stu-id="3bca5-141">Latest service pack must be installed.</span></span>
- <span data-ttu-id="3bca5-142">WMF 3,0 **får inte** vara installerat.</span><span class="sxs-lookup"><span data-stu-id="3bca5-142">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="3bca5-143">Installation av WMF 5,1 över WMF 3,0 leder till förlust av **PSModulePath** (`$env:PSModulePath`), vilket kan orsaka att andra program Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="3bca5-143">Installing WMF 5.1 over WMF 3.0 will result in the loss of the **PSModulePath** (`$env:PSModulePath`), which can cause other applications to fail.</span></span> <span data-ttu-id="3bca5-144">Innan du installerar WMF 5,1 måste du antingen avinstallera WMF 3,0 eller spara **PSModulePath** och sedan återställa den manuellt när WMF 5,1-installationen är klar.</span><span class="sxs-lookup"><span data-stu-id="3bca5-144">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the **PSModulePath** and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="3bca5-145">WMF 5,1 kräver minst [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="3bca5-145">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).</span></span>
  <span data-ttu-id="3bca5-146">Du kan installera Microsoft .NET Framework 4.5.2 genom att följa anvisningarna på hämtnings platsen.</span><span class="sxs-lookup"><span data-stu-id="3bca5-146">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="3bca5-147">Installera WMF 5,1 på Windows Server 2008 R2 och Windows 7</span><span class="sxs-lookup"><span data-stu-id="3bca5-147">Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7</span></span>

1. <span data-ttu-id="3bca5-148">Navigera till den mapp där du laddade ned ZIP-filen.</span><span class="sxs-lookup"><span data-stu-id="3bca5-148">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="3bca5-149">Högerklicka på ZIP-filen och välj **extrahera alla..** .. ZIP-filen innehåller två filer: en MSU-fil och `Install-WMF5.1.ps1` skript filen.</span><span class="sxs-lookup"><span data-stu-id="3bca5-149">Right-click on the ZIP file, and select **Extract All...**. The ZIP file contains two files: an MSU and the `Install-WMF5.1.ps1` script file.</span></span> <span data-ttu-id="3bca5-150">När du har packat upp ZIP-filen kan du kopiera innehållet till alla datorer som kör Windows 7 eller Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="3bca5-150">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="3bca5-151">När du har extraherat ZIP-filens innehåll öppnar du PowerShell som administratör och navigerar sedan till den mapp som innehåller innehållet i ZIP-filen.</span><span class="sxs-lookup"><span data-stu-id="3bca5-151">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="3bca5-152">Kör `Install-WMF5.1.ps1`-skriptet i mappen och följ instruktionerna.</span><span class="sxs-lookup"><span data-stu-id="3bca5-152">Run the `Install-WMF5.1.ps1` script in that folder, and follow the instructions.</span></span> <span data-ttu-id="3bca5-153">Det här skriptet kontrollerar kraven på den lokala datorn och installerar WMF 5,1 om kraven är uppfyllda.</span><span class="sxs-lookup"><span data-stu-id="3bca5-153">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="3bca5-154">Kraven visas nedan.</span><span class="sxs-lookup"><span data-stu-id="3bca5-154">The prerequisites are listed below.</span></span>

   <span data-ttu-id="3bca5-155">`Install-WMF5.1.ps1` använder följande parametrar för att under lätta automatisering av installationen på Windows Server 2008 R2 och Windows 7:</span><span class="sxs-lookup"><span data-stu-id="3bca5-155">`Install-WMF5.1.ps1` takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

   - <span data-ttu-id="3bca5-156">**AcceptEula**: när den här parametern ingår godkänns licens avtalet automatiskt och visas inte.</span><span class="sxs-lookup"><span data-stu-id="3bca5-156">**AcceptEula**: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
   - <span data-ttu-id="3bca5-157">**AllowRestart**: den här parametern kan endast användas om AcceptEula har angetts.</span><span class="sxs-lookup"><span data-stu-id="3bca5-157">**AllowRestart**: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="3bca5-158">Om den här parametern tas med och en omstart krävs efter installation av WMF 5,1 sker omstarten utan att du tillförar omedelbart efter att installationen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="3bca5-158">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="3bca5-159">WinRM-beroende</span><span class="sxs-lookup"><span data-stu-id="3bca5-159">WinRM Dependency</span></span>

<span data-ttu-id="3bca5-160">Windows PowerShell Desired State Configuration (DSC) är beroende av WinRM.</span><span class="sxs-lookup"><span data-stu-id="3bca5-160">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="3bca5-161">WinRM är inte aktiverat som standard på Windows Server 2008 R2 och Windows 7.</span><span class="sxs-lookup"><span data-stu-id="3bca5-161">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="3bca5-162">Kör `Set-WSManQuickConfig`i en upphöjd Windows PowerShell-session för att aktivera WinRM.</span><span class="sxs-lookup"><span data-stu-id="3bca5-162">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="3bca5-163">Installera WMF 5,1 för Windows Server 2012 R2, Windows Server 2012 och Windows 8,1</span><span class="sxs-lookup"><span data-stu-id="3bca5-163">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

### <a name="install-from-windows-file-explorer"></a><span data-ttu-id="3bca5-164">Installera från Utforskaren i Windows</span><span class="sxs-lookup"><span data-stu-id="3bca5-164">Install from Windows File Explorer</span></span>

1. <span data-ttu-id="3bca5-165">Navigera till den mapp som du laddade ned MSU-filen till.</span><span class="sxs-lookup"><span data-stu-id="3bca5-165">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="3bca5-166">Dubbelklicka på MSU för att köra det.</span><span class="sxs-lookup"><span data-stu-id="3bca5-166">Double-click the MSU to run it.</span></span>

### <a name="installing-from-the-command-prompt"></a><span data-ttu-id="3bca5-167">Installera från kommando tolken</span><span class="sxs-lookup"><span data-stu-id="3bca5-167">Installing from the Command Prompt</span></span>

1. <span data-ttu-id="3bca5-168">När du har hämtat rätt paket för datorns arkitektur öppnar du ett kommando tolks fönster med utökade användar rättigheter (kör som administratör).</span><span class="sxs-lookup"><span data-stu-id="3bca5-168">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="3bca5-169">På Server Core-installations alternativen för Windows Server 2012 R2, Windows Server 2012 eller Windows Server 2008 R2 SP1 öppnas kommando tolken med utökade användar rättigheter som standard.</span><span class="sxs-lookup"><span data-stu-id="3bca5-169">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="3bca5-170">Ändra kataloger till mappen där du har laddat ned eller kopierat WMF 5,1-installations paketet.</span><span class="sxs-lookup"><span data-stu-id="3bca5-170">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="3bca5-171">Kör något av följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="3bca5-171">Run one of the following commands:</span></span>
   - <span data-ttu-id="3bca5-172">Kör `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`på datorer som kör Windows Server 2012 R2 eller Windows 8,1 x64.</span><span class="sxs-lookup"><span data-stu-id="3bca5-172">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="3bca5-173">Kör `W2K12-KB3191565-x64.msu /quiet`på datorer som kör Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="3bca5-173">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="3bca5-174">Kör `Win8.1-KB3191564-x86.msu /quiet`på datorer som kör Windows 8,1 x86.</span><span class="sxs-lookup"><span data-stu-id="3bca5-174">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="3bca5-175">Installation av WMF 5,1 kräver en omstart.</span><span class="sxs-lookup"><span data-stu-id="3bca5-175">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="3bca5-176">Med alternativet `/quiet` startas systemet om utan varning.</span><span class="sxs-lookup"><span data-stu-id="3bca5-176">Using the `/quiet` option will reboot the system without warning.</span></span> <span data-ttu-id="3bca5-177">Använd alternativet `/norestart` för att undvika att starta om.</span><span class="sxs-lookup"><span data-stu-id="3bca5-177">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="3bca5-178">WMF 5,1 kommer dock inte att installeras förrän du har startat om.</span><span class="sxs-lookup"><span data-stu-id="3bca5-178">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
