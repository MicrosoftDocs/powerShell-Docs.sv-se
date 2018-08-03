# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="1a111-101">Installera PowerShell Core i Windows</span><span class="sxs-lookup"><span data-stu-id="1a111-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="1a111-102">MSI</span><span class="sxs-lookup"><span data-stu-id="1a111-102">MSI</span></span>

<span data-ttu-id="1a111-103">Installera PowerShell på en Windows-klienten eller Windows Server (fungerar på Windows 7 SP1, Server 2008 R2 och senare), ladda ned MSI-paketet från vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="1a111-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="1a111-104">MSI-filen som ser ut så här- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="1a111-104">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="1a111-105">När du har hämtat, dubbelklicka på installationsprogrammet och följ anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="1a111-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="1a111-106">Det finns en genväg som placeras på Start-menyn vid installationen.</span><span class="sxs-lookup"><span data-stu-id="1a111-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="1a111-107">Paketet installeras som standard till `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="1a111-107">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="1a111-108">Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="1a111-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1a111-109">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="1a111-109">Prerequisites</span></span>

<span data-ttu-id="1a111-110">Om du vill aktivera PowerShell-fjärrkommunikation via WSMan, måste följande krav uppfyllas:</span><span class="sxs-lookup"><span data-stu-id="1a111-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="1a111-111">Installera den [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner före Windows 10.</span><span class="sxs-lookup"><span data-stu-id="1a111-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="1a111-112">Det är tillgängligt via direkt ladda ned eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="1a111-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="1a111-113">Fullständigt uppdaterad (inklusive valfria paket) har system som stöds redan det installerat.</span><span class="sxs-lookup"><span data-stu-id="1a111-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="1a111-114">Installera på Windows Management Framework (WMF) 4.0 eller senare på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="1a111-114">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="1a111-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="1a111-115">ZIP</span></span>

<span data-ttu-id="1a111-116">PowerShell binära ZIP-arkiv tillhandahålls för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="1a111-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="1a111-117">Observera att du inte får kravkontrollen som i MSI-paket när du använder ZIP-arkivet.</span><span class="sxs-lookup"><span data-stu-id="1a111-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="1a111-118">Så för fjärrkommunikation via WSMan ska fungera korrekt på Windows-versioner före Windows 10, du måste se till att den [krav](#prerequisites) är uppfyllda.</span><span class="sxs-lookup"><span data-stu-id="1a111-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="1a111-119">Distribuera på Windows IoT</span><span class="sxs-lookup"><span data-stu-id="1a111-119">Deploying on Windows IoT</span></span>

<span data-ttu-id="1a111-120">Windows IoT levereras med Windows PowerShell som ska användas för att distribuera PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="1a111-120">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="1a111-121">Skapa `PSSession` till målenheten</span><span class="sxs-lookup"><span data-stu-id="1a111-121">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="1a111-122">Kopiera ZIP-paketet till enheten</span><span class="sxs-lookup"><span data-stu-id="1a111-122">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="1a111-123">Anslut till enheten och expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="1a111-123">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. <span data-ttu-id="1a111-124">Konfigurera fjärrkommunikation till PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="1a111-124">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="1a111-125">Ansluta till PowerShell Core 6-slutpunkten på enheten</span><span class="sxs-lookup"><span data-stu-id="1a111-125">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="1a111-126">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="1a111-126">Deploying on Nano Server</span></span>

<span data-ttu-id="1a111-127">Dessa instruktioner förutsätter att en version av PowerShell körs redan på Nano Server-avbildningen och att den har genererats av den [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="1a111-127">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="1a111-128">Nano Server är ett ”fjärradministrering” operativsystem.</span><span class="sxs-lookup"><span data-stu-id="1a111-128">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="1a111-129">Grundläggande binärfiler kan du distribuera med två olika metoder.</span><span class="sxs-lookup"><span data-stu-id="1a111-129">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="1a111-130">Offline - montera den virtuella Hårddisken Nano Server och packa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="1a111-130">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="1a111-131">Online - överför zip-filen via en PowerShell-Session och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="1a111-131">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="1a111-132">I båda fallen måste versionen för Windows 10 x64 ZIP paketera och kommer att behöva köra kommandona i ett ”administratör” PowerShell-instansen.</span><span class="sxs-lookup"><span data-stu-id="1a111-132">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="1a111-133">Offline distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="1a111-133">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="1a111-134">Använd din favorit zip-verktyg för att packa upp paketet till en katalog i den monterade avbildningen Nano Server.</span><span class="sxs-lookup"><span data-stu-id="1a111-134">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="1a111-135">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="1a111-135">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="1a111-136">Anslut till Inkorgen instans av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a111-136">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="1a111-137">Följ anvisningarna för att skapa en fjärrkommunikation slutpunkten med den [”en annan instans metod”](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="1a111-137">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="1a111-138">Online distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="1a111-138">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="1a111-139">Följande steg beskriver hur du distributionen av PowerShell Core till en pågående instans av Nano Server och konfigurationen av dess fjärrslutpunkten.</span><span class="sxs-lookup"><span data-stu-id="1a111-139">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="1a111-140">Ansluta till Inkorgen instans av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a111-140">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="1a111-141">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="1a111-141">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="1a111-142">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="1a111-142">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="1a111-143">Extrahera ZIP-filen</span><span class="sxs-lookup"><span data-stu-id="1a111-143">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="1a111-144">Om du vill WSMan-baserad fjärrkommunikation följer du anvisningarna för att skapa en fjärrkommunikation slutpunkt med hjälp av den [”en annan instans metod”](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="1a111-144">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="1a111-145">Instruktioner för att skapa en slutpunkt för fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="1a111-145">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="1a111-146">PowerShell Core stöder PowerShell fjärrkommunikation Protocol (PSRP) via WSMan- och SSH.</span><span class="sxs-lookup"><span data-stu-id="1a111-146">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="1a111-147">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="1a111-147">For more information, see:</span></span>

- <span data-ttu-id="1a111-148">[SSH fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="1a111-148">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="1a111-149">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="1a111-149">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="1a111-150">Instruktioner för Installation av artefakt</span><span class="sxs-lookup"><span data-stu-id="1a111-150">Artifact Installation Instructions</span></span>

<span data-ttu-id="1a111-151">Vi publicerar ett arkiv med CoreCLR bitar varje CI-version med [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="1a111-151">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="1a111-152">Installera PowerShell Core från CoreCLR artefakten:</span><span class="sxs-lookup"><span data-stu-id="1a111-152">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="1a111-153">Ladda ned ZIP-paketet från **artefakter** fliken för specifika versionen.</span><span class="sxs-lookup"><span data-stu-id="1a111-153">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="1a111-154">Avblockera ZIP-filen: Högerklicka i Utforskaren -> Egenskaper -> Kontrollera 'Avblockera' box -> tillämpa</span><span class="sxs-lookup"><span data-stu-id="1a111-154">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="1a111-155">Extrahera zipfilen till `bin` directory</span><span class="sxs-lookup"><span data-stu-id="1a111-155">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[släpper]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
