---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
contributor: keithb
title: Installera och konfigurera WMF 5.1
ms.openlocfilehash: e5590d48d467506270ccef4089513e1afade07be
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795580"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="2d6a2-103">Installera och konfigurera WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2d6a2-103">Install and Configure WMF 5.1</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="2d6a2-104">Ladda ned och installera WMF 5.1-paketet</span><span class="sxs-lookup"><span data-stu-id="2d6a2-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="2d6a2-105">Hämta WMF 5.1-paketet för operativsystemet och arkitektur som du vill installera den på:</span><span class="sxs-lookup"><span data-stu-id="2d6a2-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="2d6a2-106">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="2d6a2-106">Operating System</span></span>       | <span data-ttu-id="2d6a2-107">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="2d6a2-107">Prerequisites</span></span>           | <span data-ttu-id="2d6a2-108">Paketet länkar</span><span class="sxs-lookup"><span data-stu-id="2d6a2-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="2d6a2-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2d6a2-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="2d6a2-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="2d6a2-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="2d6a2-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2d6a2-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="2d6a2-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="2d6a2-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="2d6a2-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="2d6a2-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="2d6a2-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="2d6a2-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="2d6a2-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="2d6a2-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="2d6a2-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="2d6a2-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="2d6a2-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="2d6a2-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="2d6a2-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="2d6a2-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="2d6a2-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="2d6a2-119">Windows 7 SP1</span></span>          | <span data-ttu-id="2d6a2-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="2d6a2-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="2d6a2-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="2d6a2-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="2d6a2-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="2d6a2-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="2d6a2-129">Installera WMF 5.1 för Windows Server 2008 R2 och Windows 7</span><span class="sxs-lookup"><span data-stu-id="2d6a2-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> <span data-ttu-id="2d6a2-130">**Obs:** Installationsinstruktioner för Windows Server 2008 R2 och Windows 7 har ändrats och skiljer sig från anvisningarna för de andra paketen.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-130">**Note:** Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="2d6a2-131">Installationsinstruktioner för Windows Server 2012 R2, Windows Server 2012 och Windows 8.1 finns nedan.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="2d6a2-132">**Installera WMF 5.1 på Windows Server 2008 R2 och Windows 7**</span><span class="sxs-lookup"><span data-stu-id="2d6a2-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="2d6a2-133">Navigera till den mapp dit du hämtade ZIP-filen.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="2d6a2-134">Högerklicka på ZIP-filen och välj ”extrahera alla...”.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="2d6a2-135">ZIP-filen innehåller 2 filer: en MSU- och installera WMF5.1.PS1-skriptfilen.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="2d6a2-136">När du har packat upp ZIP-filen, kan du kopiera innehållet till en dator som kör Windows 7 eller Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="2d6a2-137">När innehållet för ZIP-filen, öppna PowerShell som administratör och navigera till mappen som innehåller innehållet i ZIP-filen.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="2d6a2-138">Kör skriptet Install-Wmf5.1.ps1 i den mappen och följ instruktionerna.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="2d6a2-139">Det här skriptet ska kontrollera krav på den lokala datorn och installera WMF 5.1 om kraven har uppfyllts.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="2d6a2-140">Kraven finns nedan.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="2d6a2-141">Installera WMF5.1.ps1 använder följande parametrar för att underlätta automatisera installationen på Windows Server 2008 R2 och Windows 7:</span><span class="sxs-lookup"><span data-stu-id="2d6a2-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="2d6a2-142">AcceptEula: När den här parametern finns LICENSAVTALET godkänns automatiskt och visas inte.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="2d6a2-143">AllowRestart: Den här parametern kan endast användas om AcceptEula har angetts.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="2d6a2-144">Om den här parametern ingår och en omstart krävs när du har installerat WMF 5.1, sker omstarten utan att fråga direkt när installationen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="2d6a2-145">**WMF 5.1 krav för Windows Server 2008 R2 SP1 och Windows 7 SP1**</span><span class="sxs-lookup"><span data-stu-id="2d6a2-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="2d6a2-146">Installation av WMF 5.1 på Windows Server 2008 R2 SP1 eller Windows 7 SP1 kräver följande:</span><span class="sxs-lookup"><span data-stu-id="2d6a2-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="2d6a2-147">Senaste servicepack måste vara installerad.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="2d6a2-148">WMF 3.0 **får inte** installeras.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="2d6a2-149">Installera WMF 5.1 via WMF 3.0 resulterar i förlust av PSModulePath, vilket kan orsaka att andra program att misslyckas.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="2d6a2-150">Innan du installerar WMF 5.1 måste antingen avinstallera WMF 3.0, eller spara PSModulePath och sedan återställa det manuellt efter att WMF 5.1-installationen är klar.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="2d6a2-151">WMF 5.1 kräver minst [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="2d6a2-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="2d6a2-152">Du kan installera Microsoft .NET Framework 4.5.2 genom att följa anvisningarna i nedladdningsplatsen.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="2d6a2-153">**WinRM-beroende**</span><span class="sxs-lookup"><span data-stu-id="2d6a2-153">**WinRM Dependency**</span></span>

<span data-ttu-id="2d6a2-154">Windows PowerShell Desired State Configuration (DSC) är beroende av WinRM.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="2d6a2-155">WinRM är inte aktiverat som standard på Windows Server 2008 R2 och Windows 7.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="2d6a2-156">Kör `Set-WSManQuickConfig`, utökade sessionen att aktivera WinRM i ett Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="2d6a2-157">Installera WMF 5.1 för Windows Server 2012 R2, Windows Server 2012 och Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="2d6a2-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

<span data-ttu-id="2d6a2-158">**Installera från Windows Explorer (eller Utforskaren i Windows Server 2012 R2 eller Windows 8.1)**</span><span class="sxs-lookup"><span data-stu-id="2d6a2-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="2d6a2-159">Navigera till den mapp dit du hämtade MSU-fil.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="2d6a2-160">Dubbelklicka på MSU att köra den.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="2d6a2-161">**Installera från Kommandotolken**</span><span class="sxs-lookup"><span data-stu-id="2d6a2-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="2d6a2-162">När du hämtat rätt paket för datorns arkitektur, öppna ett kommandotolksfönster med utökade användarrättigheter (Kör som administratör).</span><span class="sxs-lookup"><span data-stu-id="2d6a2-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="2d6a2-163">På installationsalternativet Server Core av Windows Server 2012 R2, Windows Server 2012 eller Windows Server 2008 R2 SP1 öppnas kommandotolk med förhöjd behörighet som standard.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="2d6a2-164">Ändra sökvägen till mappen dit du har hämtat eller kopierade WMF 5.1-installationspaketet.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="2d6a2-165">Kör något av följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="2d6a2-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="2d6a2-166">Kör på datorer som kör Windows Server 2012 R2 eller Windows 8.1 x64 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="2d6a2-167">Kör på datorer som kör Windows Server 2012, `W2K12-KB3191565-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="2d6a2-168">Kör på datorer som kör Windows 8.1 x86 `Win8.1-KB3191564-x86.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="2d6a2-169">Installera WMF 5.1 kräver en omstart.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="2d6a2-170">Med hjälp av den `/quiet` alternativet startar om systemet utan varning.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="2d6a2-171">Använd den `/norestart` alternativet för att undvika att starta om.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="2d6a2-172">WMF 5.1 kommer inte installeras förrän du har startats om.</span><span class="sxs-lookup"><span data-stu-id="2d6a2-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
