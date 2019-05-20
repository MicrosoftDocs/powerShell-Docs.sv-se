---
title: Installera PowerShell Core i Windows
description: Information om att installera PowerShell Core i Windows
ms.date: 08/06/2018
ms.openlocfilehash: 5a3c43e27f0027cfbeeefab33b045e618e0ff045
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854368"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="b4449-103">Installera PowerShell Core i Windows</span><span class="sxs-lookup"><span data-stu-id="b4449-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="b4449-104">Det finns flera sätt att installera PowerShell Core i Windows.</span><span class="sxs-lookup"><span data-stu-id="b4449-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b4449-105">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="b4449-105">Prerequisites</span></span>

<span data-ttu-id="b4449-106">Om du vill aktivera PowerShell-fjärrkommunikation via WSMan, måste följande krav uppfyllas:</span><span class="sxs-lookup"><span data-stu-id="b4449-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="b4449-107">Installera den [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner före Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b4449-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="b4449-108">Det är tillgängligt via direkt ladda ned eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="b4449-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="b4449-109">Fullständigt uppdaterad (inklusive valfria paket) har system som stöds redan det installerat.</span><span class="sxs-lookup"><span data-stu-id="b4449-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="b4449-110">Installera på Windows Management Framework (WMF) 4.0 eller senare på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="b4449-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="b4449-111">Läs mer om WMF [WMF översikt](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="b4449-111">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="b4449-112"><a id="msi" />Installerar MSI-paketet</span><span class="sxs-lookup"><span data-stu-id="b4449-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="b4449-113">Installera PowerShell på en Windows-klienten eller Windows Server (fungerar på Windows 7 SP1, Server 2008 R2 och senare), ladda ned MSI-paketet från vår GitHub [versioner] []-sida.</span><span class="sxs-lookup"><span data-stu-id="b4449-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span> <span data-ttu-id="b4449-114">Rulla ned till den **tillgångar** delen av den version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="b4449-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="b4449-115">Vara kan dolda i tillgångar-avsnittet så att du kan behöva klicka på för att expandera den.</span><span class="sxs-lookup"><span data-stu-id="b4449-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="b4449-116">MSI-filen som ser ut så här- `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="b4449-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="b4449-117">När du har hämtat, dubbelklicka på installationsprogrammet och följ anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="b4449-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="b4449-118">Installationsprogrammet skapar en genväg på Windows-startmenyn.</span><span class="sxs-lookup"><span data-stu-id="b4449-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="b4449-119">Paketet installeras som standard till `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="b4449-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="b4449-120">Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="b4449-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="b4449-121">Administrativ installation från kommandoraden</span><span class="sxs-lookup"><span data-stu-id="b4449-121">Administrative install from the command line</span></span>

<span data-ttu-id="b4449-122">MSI-paket kan installeras från kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="b4449-122">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="b4449-123">Detta gör att administratörer kan distribuera paket utan interaktion från användaren.</span><span class="sxs-lookup"><span data-stu-id="b4449-123">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="b4449-124">MSI-paketet för PowerShell innehåller följande egenskaper för att styra vilka installationsalternativ:</span><span class="sxs-lookup"><span data-stu-id="b4449-124">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="b4449-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** -den här egenskapen styr alternativet för att lägga till den **öppna PowerShell** objekt till på snabbmenyn i Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="b4449-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="b4449-126">**ENABLE_PSREMOTING** -den här egenskapen styr alternativ för att aktivera PowerShell-fjärrkommunikation under installationen.</span><span class="sxs-lookup"><span data-stu-id="b4449-126">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="b4449-127">**REGISTER_MANIFEST** -den här egenskapen styr alternativ för att registrera Windows-händelseloggning manifestet.</span><span class="sxs-lookup"><span data-stu-id="b4449-127">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="b4449-128">I följande exempel visar hur du obevakat installera PowerShell Core med alla installationsalternativen aktiverat.</span><span class="sxs-lookup"><span data-stu-id="b4449-128">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="b4449-129">En fullständig lista över kommandoradsalternativ för Msiexec.exe Se [kommandoradsalternativ](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="b4449-129">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="b4449-130"><a id="zip" />Installerar ZIP-paketet</span><span class="sxs-lookup"><span data-stu-id="b4449-130"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="b4449-131">PowerShell binära ZIP-arkiv tillhandahålls för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="b4449-131">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="b4449-132">Observera att du inte får kravkontrollen som i MSI-paket när du använder ZIP-arkivet.</span><span class="sxs-lookup"><span data-stu-id="b4449-132">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="b4449-133">För fjärrkommunikation via WSMan ska fungera korrekt, att se till att du har uppfyllt de [krav](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="b4449-133">For remoting over WSMan to work properly,, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="b4449-134">Distribuera på Windows IoT</span><span class="sxs-lookup"><span data-stu-id="b4449-134">Deploying on Windows IoT</span></span>

<span data-ttu-id="b4449-135">Windows IoT levereras med Windows PowerShell som ska användas för att distribuera PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="b4449-135">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="b4449-136">Skapa `PSSession` till målenheten</span><span class="sxs-lookup"><span data-stu-id="b4449-136">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="b4449-137">Kopiera ZIP-paketet till enheten</span><span class="sxs-lookup"><span data-stu-id="b4449-137">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="b4449-138">Anslut till enheten och expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="b4449-138">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="b4449-139">Konfigurera fjärrkommunikation till PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="b4449-139">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="b4449-140">Ansluta till PowerShell Core 6-slutpunkten på enheten</span><span class="sxs-lookup"><span data-stu-id="b4449-140">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="b4449-141">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="b4449-141">Deploying on Nano Server</span></span>

<span data-ttu-id="b4449-142">Dessa instruktioner förutsätter att en version av PowerShell körs redan på Nano Server-avbildningen och att den har genererats av den [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="b4449-142">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="b4449-143">Nano Server är ett ”fjärradministrering” operativsystem.</span><span class="sxs-lookup"><span data-stu-id="b4449-143">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="b4449-144">Grundläggande binärfiler kan du distribuera med två olika metoder.</span><span class="sxs-lookup"><span data-stu-id="b4449-144">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="b4449-145">Offline - montera den virtuella Hårddisken Nano Server och packa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="b4449-145">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="b4449-146">Online - överför zip-filen via en PowerShell-Session och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="b4449-146">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="b4449-147">I båda fallen måste versionen för Windows 10 x64 ZIP paketera och kommer att behöva köra kommandona i ett ”administratör” PowerShell-instansen.</span><span class="sxs-lookup"><span data-stu-id="b4449-147">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="b4449-148">Offline distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b4449-148">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="b4449-149">Använd din favorit zip-verktyg för att packa upp paketet till en katalog i den monterade avbildningen Nano Server.</span><span class="sxs-lookup"><span data-stu-id="b4449-149">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="b4449-150">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="b4449-150">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="b4449-151">Anslut till Inkorgen instans av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4449-151">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="b4449-152">Följ anvisningarna för att skapa en fjärrkommunikation slutpunkten med den [”en annan instans metod”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="b4449-152">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="b4449-153">Online distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b4449-153">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="b4449-154">Följande steg beskriver hur du distributionen av PowerShell Core till en pågående instans av Nano Server och konfigurationen av dess fjärrslutpunkten.</span><span class="sxs-lookup"><span data-stu-id="b4449-154">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="b4449-155">Ansluta till Inkorgen instans av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4449-155">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="b4449-156">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="b4449-156">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="b4449-157">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="b4449-157">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="b4449-158">Extrahera ZIP-filen</span><span class="sxs-lookup"><span data-stu-id="b4449-158">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="b4449-159">Om du vill WSMan-baserad fjärrkommunikation följer du anvisningarna för att skapa en fjärrkommunikation slutpunkt med hjälp av den [”en annan instans metod”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="b4449-159">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="b4449-160">Så här skapar du en slutpunkt för fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="b4449-160">How to create a remoting endpoint</span></span>

<span data-ttu-id="b4449-161">PowerShell Core stöder PowerShell fjärrkommunikation Protocol (PSRP) via WSMan- och SSH.</span><span class="sxs-lookup"><span data-stu-id="b4449-161">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="b4449-162">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="b4449-162">For more information, see:</span></span>

- <span data-ttu-id="b4449-163">[SSH fjärrkommunikation i PowerShell Core] [ssh-fjärrkommunikation]</span><span class="sxs-lookup"><span data-stu-id="b4449-163">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="b4449-164">[WSMan-fjärrkommunikation i PowerShell Core] [wsman-fjärrkommunikation]</span><span class="sxs-lookup"><span data-stu-id="b4449-164">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->
[släpper]: https://github.com/PowerShell/PowerShell/releases [ssh-fjärrkommunikation]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman-fjärrkommunikation]:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
