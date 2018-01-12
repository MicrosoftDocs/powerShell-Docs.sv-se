# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="226c2-101">Installera PowerShell Core i Windows</span><span class="sxs-lookup"><span data-stu-id="226c2-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="226c2-102">MSI</span><span class="sxs-lookup"><span data-stu-id="226c2-102">MSI</span></span>

<span data-ttu-id="226c2-103">Installera PowerShell på en Windows-klienten eller Windows Server (fungerar på Server 2008 R2, Windows 7 SP1 och senare), ladda ned MSI-paketet från vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="226c2-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="226c2-104">MSI-filen ser ut så här-`PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="226c2-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="226c2-105">När du har hämtat, dubbelklickar du på installationsprogrammet och följ anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="226c2-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="226c2-106">Det finns en genväg som placerats i Start-menyn vid installationen.</span><span class="sxs-lookup"><span data-stu-id="226c2-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

* <span data-ttu-id="226c2-107">Paketet installeras som standard till`$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="226c2-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
* <span data-ttu-id="226c2-108">Du kan starta PowerShell via Start-menyn eller`$env:ProgramFiles\PowerShell\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="226c2-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="226c2-109">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="226c2-109">Prerequisites</span></span>

<span data-ttu-id="226c2-110">Om du vill aktivera PowerShell-fjärrkommunikation över WSMan, måste följande krav uppfyllas:</span><span class="sxs-lookup"><span data-stu-id="226c2-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

* <span data-ttu-id="226c2-111">Installera den [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner före Windows 10.</span><span class="sxs-lookup"><span data-stu-id="226c2-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="226c2-112">Det är tillgängligt via direkt hämta eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="226c2-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="226c2-113">Korrigerade fullständigt (inklusive valfria paket), har stöds system redan det installeras.</span><span class="sxs-lookup"><span data-stu-id="226c2-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
* <span data-ttu-id="226c2-114">Installera Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) eller senare ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="226c2-114">Install the Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) or newer ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="226c2-115">ZIP-</span><span class="sxs-lookup"><span data-stu-id="226c2-115">ZIP</span></span>

<span data-ttu-id="226c2-116">PowerShell binära ZIP-arkiv som aktivera avancerade distribueringsscenarier.</span><span class="sxs-lookup"><span data-stu-id="226c2-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="226c2-117">Observera att du inte får kravkontrollen som MSI-paket när du använder ZIP-arkivet.</span><span class="sxs-lookup"><span data-stu-id="226c2-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="226c2-118">Så i ordning för fjärrkörning via WSMan ska fungera på Windows-versioner före Windows 10, måste du kontrollera att den [krav](#prerequisites) är uppfyllda.</span><span class="sxs-lookup"><span data-stu-id="226c2-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="226c2-119">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="226c2-119">Deploying on Nano Server</span></span>

<span data-ttu-id="226c2-120">Dessa instruktioner förutsätter att en version av PowerShell körs redan på Nano Server-avbildning och har genererats av den [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="226c2-120">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="226c2-121">Nano Server är ett ”fjärradministrerade” operativsystem och distribution av PowerShell Core binärfiler kan inträffa på två olika sätt:</span><span class="sxs-lookup"><span data-stu-id="226c2-121">Nano Server is a "headless" OS and deployment of PowerShell Core binaries can happen in two different ways:</span></span>

1. <span data-ttu-id="226c2-122">Offline - Montera VHD: N Nano Server och packa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="226c2-122">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="226c2-123">Online - överför zip-filen via en PowerShell-Session och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="226c2-123">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="226c2-124">I båda fallen måste Windows 10 x64 Zip-versionen paketera och måste köra kommandona i ett ”administratör” PowerShell-instansen.</span><span class="sxs-lookup"><span data-stu-id="226c2-124">In both cases, you will need the Windows 10 x64 Zip release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="226c2-125">Offline distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="226c2-125">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="226c2-126">Använd din favorit zip-verktyg för att packa upp paketet till en katalog i den monterade avbildningen Nano Server.</span><span class="sxs-lookup"><span data-stu-id="226c2-126">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="226c2-127">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="226c2-127">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="226c2-128">Anslut till Inkorgen instans av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="226c2-128">Connect to the inbox instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="226c2-129">Följ instruktionerna för att skapa en fjärrkommunikation slutpunkten med hjälp av den [en annan instans metod](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="226c2-129">Follow the instructions to create a remoting endpoint using the [another instance technique](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="226c2-130">Online distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="226c2-130">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="226c2-131">Följande steg vägleder dig genom distributionen av PowerShell Core till en instans som körs av Nano Server och konfigurationen av dess fjärrslutpunkten.</span><span class="sxs-lookup"><span data-stu-id="226c2-131">The following steps will guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

* <span data-ttu-id="226c2-132">Ansluta till Inkorgen instans av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="226c2-132">Connect to the inbox instance of Windows PowerShell</span></span>

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* <span data-ttu-id="226c2-133">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="226c2-133">Copy the file to the Nano Server instance</span></span>

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* <span data-ttu-id="226c2-134">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="226c2-134">Enter the session</span></span>

```powershell
Enter-PSSession $session
```

* <span data-ttu-id="226c2-135">Extrahera Zip-filen</span><span class="sxs-lookup"><span data-stu-id="226c2-135">Extract the Zip file</span></span>

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* <span data-ttu-id="226c2-136">Om du vill WSMan-baserad remoting, följ instruktionerna för att skapa ett fjärrkommunikation slutpunkt med det [en annan instans metod](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="226c2-136">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the [another instance technique](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="226c2-137">Instruktioner för att skapa en slutpunkt för fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="226c2-137">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="226c2-138">PowerShell Core stöder PowerShell fjärrkommunikation Protocol (PSRP) över SSH- och WSMan.</span><span class="sxs-lookup"><span data-stu-id="226c2-138">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="226c2-139">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="226c2-139">For more information, see:</span></span>

* <span data-ttu-id="226c2-140">[SSH fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="226c2-140">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="226c2-141">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="226c2-141">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="226c2-142">Installationsinstruktioner för artefakt</span><span class="sxs-lookup"><span data-stu-id="226c2-142">Artifact Installation Instructions</span></span>

<span data-ttu-id="226c2-143">Vi publicerar ett arkiv med CoreCLR bitar på varje CI-version med [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="226c2-143">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

## <a name="coreclr-artifacts"></a><span data-ttu-id="226c2-144">CoreCLR artefakter</span><span class="sxs-lookup"><span data-stu-id="226c2-144">CoreCLR Artifacts</span></span>

* <span data-ttu-id="226c2-145">Hämta zip-paketet från **artefakter** fliken för en viss version.</span><span class="sxs-lookup"><span data-stu-id="226c2-145">Download zip package from **artifacts** tab of the particular build.</span></span>
* <span data-ttu-id="226c2-146">Avblockera zip-filen: Högerklicka i Utforskaren -> Egenskaper -> Kontrollera 'Avblockera' box -> tillämpa</span><span class="sxs-lookup"><span data-stu-id="226c2-146">Unblock zip file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
* <span data-ttu-id="226c2-147">Extrahera zipfilen till `bin` directory</span><span class="sxs-lookup"><span data-stu-id="226c2-147">Extract zip file to `bin` directory</span></span>
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[släpper]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
