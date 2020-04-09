---
title: Installera PowerShell i Windows
description: Information om hur du installerar PowerShell på Windows
ms.date: 08/06/2018
ms.openlocfilehash: 17b2c7c51e54cea42ee68dc1812ffe89654806fc
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977496"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="e2980-103">Installera PowerShell i Windows</span><span class="sxs-lookup"><span data-stu-id="e2980-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="e2980-104">Det finns flera sätt att installera PowerShell i Windows.</span><span class="sxs-lookup"><span data-stu-id="e2980-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2980-105">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="e2980-105">Prerequisites</span></span>

<span data-ttu-id="e2980-106">Den senaste versionen av PowerShell stöds på Windows 7 SP1, Server 2008 R2 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="e2980-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="e2980-107">Om du vill aktivera PowerShell-fjärrkommunikation över WSMan måste följande krav vara uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="e2980-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="e2980-108">Installera [Universal C runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner predating Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e2980-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="e2980-109">Den är tillgänglig via direkt hämtning eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="e2980-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="e2980-110">Fullständigt installerade system har redan det här paketet installerat.</span><span class="sxs-lookup"><span data-stu-id="e2980-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="e2980-111">Installera Windows Management Framework (WMF) 4,0 eller senare på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="e2980-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="e2980-112">Mer information om WMF finns i [Översikt över WMF](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="e2980-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="e2980-113">Ladda ned installations paketet</span><span class="sxs-lookup"><span data-stu-id="e2980-113">Download the installer package</span></span>

<span data-ttu-id="e2980-114">Installera PowerShell på Windows genom att ladda ned installations paketet från vår GitHub- [releases][releases] -sida.</span><span class="sxs-lookup"><span data-stu-id="e2980-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="e2980-115">Rulla ned till **till gångar** -avsnittet på sidan version.</span><span class="sxs-lookup"><span data-stu-id="e2980-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="e2980-116">Avsnittet **till gångar** kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="e2980-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="e2980-117"><a id="msi" />installera MSI-paketet</span><span class="sxs-lookup"><span data-stu-id="e2980-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="e2980-118">MSI-filen ser ut som `PowerShell-<version>-win-<os-arch>.msi`.</span><span class="sxs-lookup"><span data-stu-id="e2980-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="e2980-119">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e2980-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="e2980-120">När du har laddat ned dubbelklickar du på installations programmet och följer anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="e2980-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="e2980-121">Installations programmet skapar en genväg på Start-menyn i Windows.</span><span class="sxs-lookup"><span data-stu-id="e2980-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="e2980-122">Som standard installeras paketet på `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="e2980-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="e2980-123">Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="e2980-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="e2980-124">PowerShell 7 installeras i en ny katalog och körs sida vid sida med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="e2980-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="e2980-125">För PowerShell Core 6. x är PowerShell 7 en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="e2980-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="e2980-126">PowerShell 7 installeras för att `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="e2980-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="e2980-127">Mappen `$env:ProgramFiles\PowerShell\7` läggs till i `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="e2980-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="e2980-128">Mappen `$env:ProgramFiles\PowerShell\6` tas bort</span><span class="sxs-lookup"><span data-stu-id="e2980-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="e2980-129">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av [zip-installations](#zip) metoden.</span><span class="sxs-lookup"><span data-stu-id="e2980-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="e2980-130">Administrativ installation från kommando raden</span><span class="sxs-lookup"><span data-stu-id="e2980-130">Administrative install from the command line</span></span>

<span data-ttu-id="e2980-131">MSI-paket kan installeras från kommando raden och gör det möjligt för administratörer att distribuera paket utan användar interaktion.</span><span class="sxs-lookup"><span data-stu-id="e2980-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="e2980-132">MSI-paketet innehåller följande egenskaper för att kontrol lera installations alternativen:</span><span class="sxs-lookup"><span data-stu-id="e2980-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="e2980-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – den här egenskapen styr alternativet för att lägga till det **Öppna PowerShell** -objektet i snabb menyn i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="e2980-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="e2980-134">**ENABLE_PSREMOTING** – den här egenskapen styr alternativet för att aktivera PowerShell-fjärrkommunikation under installationen.</span><span class="sxs-lookup"><span data-stu-id="e2980-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="e2980-135">**REGISTER_MANIFEST** – den här egenskapen styr alternativet för registrering av Windows händelse loggnings manifestet.</span><span class="sxs-lookup"><span data-stu-id="e2980-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="e2980-136">I följande exempel visas hur du tyst installerar PowerShell med alla installations alternativ aktiverade.</span><span class="sxs-lookup"><span data-stu-id="e2980-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="e2980-137">En fullständig lista över kommando rads alternativ för `Msiexec.exe`finns i [kommando rads alternativ](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="e2980-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="e2980-138"><a id="msix" />installera MSIX-paketet</span><span class="sxs-lookup"><span data-stu-id="e2980-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="e2980-139">Om du vill installera MSIX-paketet manuellt på en Windows 10-klient laddar du ned MSIX-paketet från vår GitHub [releases][releases] -sida.</span><span class="sxs-lookup"><span data-stu-id="e2980-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="e2980-140">Rulla ned till **till gångar** -avsnittet i den version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="e2980-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="e2980-141">Avsnittet till gångar kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="e2980-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="e2980-142">MSIX-filen ser ut så här – `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="e2980-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="e2980-143">Du måste använda `Add-AppxPackage`-cmdleten för att installera paketet.</span><span class="sxs-lookup"><span data-stu-id="e2980-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="e2980-144">MSIX-paketet har ännu inte släppts.</span><span class="sxs-lookup"><span data-stu-id="e2980-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="e2980-145">När paketet har släppts är paketet tillgängligt i Microsoft Store och från sidan GitHub- [versioner][releases] .</span><span class="sxs-lookup"><span data-stu-id="e2980-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="e2980-146"><a id="zip" />installation av ZIP-paketet</span><span class="sxs-lookup"><span data-stu-id="e2980-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="e2980-147">Det finns PowerShell-Arkiv för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="e2980-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="e2980-148">Installation av ZIP-arkivet kontrollerar inte kraven som MSI-paketen gör.</span><span class="sxs-lookup"><span data-stu-id="e2980-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="e2980-149">Se till att du uppfyller [kraven](#prerequisites)för fjärr kommunikation över WSMan för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="e2980-149">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="e2980-150">Distribuera i Windows 10 IoT Enterprise</span><span class="sxs-lookup"><span data-stu-id="e2980-150">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="e2980-151">Windows 10 IoT Enterprise levereras med Windows PowerShell, som vi kan använda för att distribuera PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="e2980-151">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="e2980-152">Skapa `PSSession` till mål enhet</span><span class="sxs-lookup"><span data-stu-id="e2980-152">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="e2980-153">Kopiera ZIP-paketet till enheten</span><span class="sxs-lookup"><span data-stu-id="e2980-153">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="e2980-154">Anslut till enheten och Expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="e2980-154">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="e2980-155">Konfigurera fjärr kommunikation till PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="e2980-155">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="e2980-156">Anslut till PowerShell 7-slutpunkt på enhet</span><span class="sxs-lookup"><span data-stu-id="e2980-156">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```
## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="e2980-157">Distribuera på Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="e2980-157">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="e2980-158">Windows 10 IoT Core lägger till Windows PowerShell när du inkluderar *IOT_POWERSHELL* funktion som vi kan använda för att distribuera PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="e2980-158">Windows 10 IoT Core adds Windows PowerShell when you include *IOT_POWERSHELL* feature, which we can use to deploy PowerShell 7.</span></span>
<span data-ttu-id="e2980-159">Stegen som definieras ovan för Windows 10 IoT Enterprise kan också följas av IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e2980-159">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="e2980-160">För att lägga till den senaste PowerShell-versionen i leverans avbildningen använder du kommandot [import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) för att inkludera paketet i workarea och lägga till *OPENSRC_POWERSHELL* funktion i avbildningen.</span><span class="sxs-lookup"><span data-stu-id="e2980-160">For adding the latest powershell in the shipping image, use [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) command to include the package in the workarea and add *OPENSRC_POWERSHELL* feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="e2980-161">Windows PowerShell läggs inte till i ARM64-arkitekturen när du tar med *IOT_POWERSHELL*.</span><span class="sxs-lookup"><span data-stu-id="e2980-161">For ARM64 architecture, Windows Powershell is not added when you include *IOT_POWERSHELL*.</span></span> <span data-ttu-id="e2980-162">Det innebär att zip-baserad installation inte fungerar.</span><span class="sxs-lookup"><span data-stu-id="e2980-162">So the zip based install will not work.</span></span>
> <span data-ttu-id="e2980-163">Du måste använda kommandot Import-PSCoreRelease för att lägga till det i avbildningen.</span><span class="sxs-lookup"><span data-stu-id="e2980-163">You will need to use Import-PSCoreRelease command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="e2980-164">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="e2980-164">Deploying on Nano Server</span></span>

<span data-ttu-id="e2980-165">Dessa instruktioner förutsätter att Nano-servern är ett "" "" "-"-OS som har en version av PowerShell som redan körs på den.</span><span class="sxs-lookup"><span data-stu-id="e2980-165">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="e2980-166">Mer information finns i dokumentationen för [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) .</span><span class="sxs-lookup"><span data-stu-id="e2980-166">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="e2980-167">PowerShell-binärfiler kan distribueras med två olika metoder.</span><span class="sxs-lookup"><span data-stu-id="e2980-167">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="e2980-168">Offline – montera den virtuella hård disken för Nano Server och zippa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="e2980-168">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="e2980-169">Överför zip-filen via en PowerShell-session online och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="e2980-169">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="e2980-170">I båda fallen behöver du paketet Windows 10 x64 ZIP release.</span><span class="sxs-lookup"><span data-stu-id="e2980-170">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="e2980-171">Kör kommandona i en "administratör"-instans av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2980-171">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="e2980-172">Offline-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2980-172">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="e2980-173">Använd ditt favorit-zip-verktyg för att packa upp paketet till en katalog i den monterade Nano Server-avbildningen.</span><span class="sxs-lookup"><span data-stu-id="e2980-173">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="e2980-174">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="e2980-174">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="e2980-175">Anslut till inkorg-instansen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2980-175">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="e2980-176">Följ instruktionerna för att skapa en fjärran sluten slut punkt med hjälp av ["en annan instans teknik"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="e2980-176">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="e2980-177">Online-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2980-177">Online Deployment of PowerShell</span></span>

<span data-ttu-id="e2980-178">Distribuera PowerShell till Nano Server med hjälp av följande steg.</span><span class="sxs-lookup"><span data-stu-id="e2980-178">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="e2980-179">Anslut till inkorg-instansen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2980-179">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="e2980-180">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="e2980-180">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="e2980-181">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="e2980-181">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="e2980-182">Extrahera ZIP-filen</span><span class="sxs-lookup"><span data-stu-id="e2980-182">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="e2980-183">Om du vill använda WSMan-baserad fjärr kommunikation följer du anvisningarna för att skapa en slut punkt för fjärr kommunikation med hjälp av ["en annan instans teknik"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="e2980-183">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="e2980-184">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="e2980-184">Install as a .NET Global tool</span></span>

<span data-ttu-id="e2980-185">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="e2980-185">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="e2980-186">Installations programmet för dotNET-verktyget lägger till `$env:USERPROFILE\dotnet\tools` i din `$env:PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="e2980-186">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="e2980-187">Men det gränssnitt som körs har inte den uppdaterade `$env:PATH`.</span><span class="sxs-lookup"><span data-stu-id="e2980-187">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="e2980-188">Du kan starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="e2980-188">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="e2980-189">Så här skapar du en fjärran sluten slut punkt</span><span class="sxs-lookup"><span data-stu-id="e2980-189">How to create a remoting endpoint</span></span>

<span data-ttu-id="e2980-190">PowerShell stöder PowerShell Remoting-protokollet (PSRP) via både WSMan och SSH.</span><span class="sxs-lookup"><span data-stu-id="e2980-190">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="e2980-191">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="e2980-191">For more information, see:</span></span>

- <span data-ttu-id="e2980-192">[SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="e2980-192">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="e2980-193">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="e2980-193">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
