---
title: Installera PowerShell Core i Windows
description: Information om att installera PowerShell Core i Windows
ms.date: 08/06/2018
ms.openlocfilehash: 450a38a1ef2e2890059094774fcc3f2ad4fcda6e
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/30/2019
ms.locfileid: "58748960"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="4f5c7-103">Installera PowerShell Core i Windows</span><span class="sxs-lookup"><span data-stu-id="4f5c7-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="4f5c7-104">MSI</span><span class="sxs-lookup"><span data-stu-id="4f5c7-104">MSI</span></span>

<span data-ttu-id="4f5c7-105">Installera PowerShell på en Windows-klienten eller Windows Server (fungerar på Windows 7 SP1, Server 2008 R2 och senare), ladda ned MSI-paketet från vår GitHub [Versioner][] sidan.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>  <span data-ttu-id="4f5c7-106">Rulla ned till den **tillgångar** delen av den version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-106">Scroll down to the **Assets** section of the Release you want to install.</span></span>  <span data-ttu-id="4f5c7-107">Vara kan dolda i tillgångar-avsnittet så att du kan behöva klicka på för att expandera den.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-107">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="4f5c7-108">MSI-filen som ser ut så här- `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="4f5c7-108">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="4f5c7-109">När du har hämtat, dubbelklicka på installationsprogrammet och följ anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-109">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="4f5c7-110">Det finns en genväg som placeras på Start-menyn vid installationen.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-110">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="4f5c7-111">Paketet installeras som standard till `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="4f5c7-111">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="4f5c7-112">Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="4f5c7-112">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="4f5c7-113">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="4f5c7-113">Prerequisites</span></span>

<span data-ttu-id="4f5c7-114">Om du vill aktivera PowerShell-fjärrkommunikation via WSMan, måste följande krav uppfyllas:</span><span class="sxs-lookup"><span data-stu-id="4f5c7-114">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="4f5c7-115">Installera den [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner före Windows 10.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-115">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="4f5c7-116">Det är tillgängligt via direkt ladda ned eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-116">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="4f5c7-117">Fullständigt uppdaterad (inklusive valfria paket) har system som stöds redan det installerat.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-117">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="4f5c7-118">Installera på Windows Management Framework (WMF) 4.0 eller senare på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-118">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="4f5c7-119">ZIP</span><span class="sxs-lookup"><span data-stu-id="4f5c7-119">ZIP</span></span>

<span data-ttu-id="4f5c7-120">PowerShell binära ZIP-arkiv tillhandahålls för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-120">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="4f5c7-121">Observera att du inte får kravkontrollen som i MSI-paket när du använder ZIP-arkivet.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-121">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="4f5c7-122">Så för fjärrkommunikation via WSMan ska fungera korrekt på Windows-versioner före Windows 10, du måste se till att den [krav](#prerequisites) är uppfyllda.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-122">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="4f5c7-123">Distribuera på Windows IoT</span><span class="sxs-lookup"><span data-stu-id="4f5c7-123">Deploying on Windows IoT</span></span>

<span data-ttu-id="4f5c7-124">Windows IoT levereras med Windows PowerShell som ska användas för att distribuera PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-124">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="4f5c7-125">Skapa `PSSession` till målenheten</span><span class="sxs-lookup"><span data-stu-id="4f5c7-125">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="4f5c7-126">Kopiera ZIP-paketet till enheten</span><span class="sxs-lookup"><span data-stu-id="4f5c7-126">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="4f5c7-127">Anslut till enheten och expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="4f5c7-127">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="4f5c7-128">Konfigurera fjärrkommunikation till PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="4f5c7-128">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="4f5c7-129">Ansluta till PowerShell Core 6-slutpunkten på enheten</span><span class="sxs-lookup"><span data-stu-id="4f5c7-129">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="4f5c7-130">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="4f5c7-130">Deploying on Nano Server</span></span>

<span data-ttu-id="4f5c7-131">Dessa instruktioner förutsätter att en version av PowerShell körs redan på Nano Server-avbildningen och att den har genererats av den [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="4f5c7-131">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="4f5c7-132">Nano Server är ett ”fjärradministrering” operativsystem.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-132">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="4f5c7-133">Grundläggande binärfiler kan du distribuera med två olika metoder.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-133">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="4f5c7-134">Offline - montera den virtuella Hårddisken Nano Server och packa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-134">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="4f5c7-135">Online - överför zip-filen via en PowerShell-Session och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-135">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="4f5c7-136">I båda fallen måste versionen för Windows 10 x64 ZIP paketera och kommer att behöva köra kommandona i ett ”administratör” PowerShell-instansen.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-136">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="4f5c7-137">Offline distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="4f5c7-137">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="4f5c7-138">Använd din favorit zip-verktyg för att packa upp paketet till en katalog i den monterade avbildningen Nano Server.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-138">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="4f5c7-139">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-139">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="4f5c7-140">Anslut till Inkorgen instans av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-140">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="4f5c7-141">Följ anvisningarna för att skapa en fjärrkommunikation slutpunkten med den [”en annan instans metod”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="4f5c7-141">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="4f5c7-142">Online distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="4f5c7-142">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="4f5c7-143">Följande steg beskriver hur du distributionen av PowerShell Core till en pågående instans av Nano Server och konfigurationen av dess fjärrslutpunkten.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-143">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="4f5c7-144">Ansluta till Inkorgen instans av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f5c7-144">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="4f5c7-145">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="4f5c7-145">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="4f5c7-146">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="4f5c7-146">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="4f5c7-147">Extrahera ZIP-filen</span><span class="sxs-lookup"><span data-stu-id="4f5c7-147">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="4f5c7-148">Om du vill WSMan-baserad fjärrkommunikation följer du anvisningarna för att skapa en fjärrkommunikation slutpunkt med hjälp av den [”en annan instans metod”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="4f5c7-148">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="4f5c7-149">Instruktioner för att skapa en slutpunkt för fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="4f5c7-149">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="4f5c7-150">PowerShell Core stöder PowerShell fjärrkommunikation Protocol (PSRP) via WSMan- och SSH.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-150">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="4f5c7-151">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="4f5c7-151">For more information, see:</span></span>

- <span data-ttu-id="4f5c7-152">[SSH fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="4f5c7-152">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="4f5c7-153">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="4f5c7-153">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="4f5c7-154">Instruktioner för Installation av artefakt</span><span class="sxs-lookup"><span data-stu-id="4f5c7-154">Artifact Installation Instructions</span></span>

<span data-ttu-id="4f5c7-155">Vi publicerar ett arkiv med CoreCLR bitar varje CI-version med [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="4f5c7-155">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="4f5c7-156">Installera PowerShell Core från CoreCLR artefakten:</span><span class="sxs-lookup"><span data-stu-id="4f5c7-156">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="4f5c7-157">Ladda ned ZIP-paketet från **artefakter** fliken för specifika versionen.</span><span class="sxs-lookup"><span data-stu-id="4f5c7-157">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="4f5c7-158">Avblockera ZIP-filen: Högerklicka i Utforskaren -> Egenskaper -> Kontrollera 'Avblockera' box -> tillämpa</span><span class="sxs-lookup"><span data-stu-id="4f5c7-158">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="4f5c7-159">Extrahera zipfilen till `bin` directory</span><span class="sxs-lookup"><span data-stu-id="4f5c7-159">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[Versioner]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
