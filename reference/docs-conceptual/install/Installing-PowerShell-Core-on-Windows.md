---
title: Installera PowerShell Core i Windows
description: Information om hur du installerar PowerShell core i Windows
ms.date: 08/06/2018
ms.openlocfilehash: 00a1d8064a3c1ec6608a46415bbabb8d98d880f0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416778"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="1bfdb-103">Installera PowerShell Core i Windows</span><span class="sxs-lookup"><span data-stu-id="1bfdb-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="1bfdb-104">Det finns flera sätt att installera PowerShell core i Windows.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

> [!TIP]
> <span data-ttu-id="1bfdb-105">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="1bfdb-105">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a><span data-ttu-id="1bfdb-106">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="1bfdb-106">Prerequisites</span></span>

<span data-ttu-id="1bfdb-107">Om du vill aktivera PowerShell-fjärrkommunikation över WSMan måste följande krav vara uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="1bfdb-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="1bfdb-108">Installera [Universal C-körningen](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner före Windows 10.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="1bfdb-109">Den är tillgänglig via direkt hämtning eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-109">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="1bfdb-110">Fullständigt uppdaterad (inklusive valfria paket) har system som stöds redan installerat.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-110">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="1bfdb-111">Installera Windows Management Framework (WMF) 4,0 eller senare på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="1bfdb-112">Mer information om WMF finns i [Översikt över WMF](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="1bfdb-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="1bfdb-113"><a id="msi" />installera MSI-paketet</span><span class="sxs-lookup"><span data-stu-id="1bfdb-113"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="1bfdb-114">Om du vill installera PowerShell på en Windows-klient eller Windows Server (fungerar på Windows 7 SP1, Server 2008 R2 och senare) laddar du ned MSI-paketet från vår GitHub [releases][releases] -sida.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-114">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="1bfdb-115">Rulla ned till **till gångar** -avsnittet i den version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-115">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="1bfdb-116">Avsnittet till gångar kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-116">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="1bfdb-117">MSI-filen ser ut så här – `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="1bfdb-117">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="1bfdb-118">När du har laddat ned dubbelklickar du på installations programmet och följer anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-118">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="1bfdb-119">Installations programmet skapar en genväg på Start-menyn i Windows.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-119">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="1bfdb-120">Som standard installeras paketet på `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="1bfdb-120">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="1bfdb-121">Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="1bfdb-121">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="1bfdb-122">Administrativ installation från kommando raden</span><span class="sxs-lookup"><span data-stu-id="1bfdb-122">Administrative install from the command line</span></span>

<span data-ttu-id="1bfdb-123">MSI-paket kan installeras från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-123">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="1bfdb-124">Detta gör att administratörer kan distribuera paket utan användar interaktion.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-124">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="1bfdb-125">MSI-paketet för PowerShell innehåller följande egenskaper för att kontrol lera installations alternativen:</span><span class="sxs-lookup"><span data-stu-id="1bfdb-125">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="1bfdb-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – den här egenskapen styr alternativet för att lägga till det **Öppna PowerShell** -objektet i snabb menyn i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="1bfdb-127">**ENABLE_PSREMOTING** – den här egenskapen styr alternativet för att aktivera PowerShell-fjärrkommunikation under installationen.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-127">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="1bfdb-128">**REGISTER_MANIFEST** – den här egenskapen styr alternativet för registrering av Windows händelse loggnings manifestet.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-128">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="1bfdb-129">I följande exempel visas hur du tyst installerar PowerShell Core med alla installations alternativ aktiverade.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-129">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="1bfdb-130">En fullständig lista över kommando rads alternativ för msiexec. exe finns i [kommando rads alternativ](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="1bfdb-130">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idmsix-installing-the-msix-package"></a><span data-ttu-id="1bfdb-131"><a id="msix" />installera MSIX-paketet</span><span class="sxs-lookup"><span data-stu-id="1bfdb-131"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="1bfdb-132">Om du vill installera MSIX-paketet manuellt på en Windows 10-klient laddar du ned MSIX-paketet från vår GitHub [releases][releases] -sida.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-132">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="1bfdb-133">Rulla ned till **till gångar** -avsnittet i den version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-133">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="1bfdb-134">Avsnittet till gångar kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-134">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="1bfdb-135">MSI-filen ser ut så här – `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="1bfdb-135">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="1bfdb-136">När du har hämtat kan du inte bara dubbelklicka på installations programmet eftersom det här paketet kräver att du använder icke-virtualiserade resurser.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-136">Once downloaded, you cannot simply double-click on the installer as this package requires use of un-virtualized resources.</span></span>  <span data-ttu-id="1bfdb-137">För att installera måste du använda `Add-AppxPackage`-cmdlet:</span><span class="sxs-lookup"><span data-stu-id="1bfdb-137">To install, you must use the `Add-AppxPackage` cmdlet:</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="1bfdb-138"><a id="zip" />installation av ZIP-paketet</span><span class="sxs-lookup"><span data-stu-id="1bfdb-138"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="1bfdb-139">Det finns PowerShell-Arkiv för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-139">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="1bfdb-140">Observera att när du använder ZIP-arkivet visas inte krav kontrollen som i MSI-paketet.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-140">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="1bfdb-141">Se till att du uppfyller [kraven](#prerequisites)för fjärr kommunikation över WSMan för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-141">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="1bfdb-142">Distribuera på Windows IoT</span><span class="sxs-lookup"><span data-stu-id="1bfdb-142">Deploying on Windows IoT</span></span>

<span data-ttu-id="1bfdb-143">Windows IoT levereras redan med Windows PowerShell som vi ska använda för att distribuera PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-143">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="1bfdb-144">Skapa `PSSession` till mål enhet</span><span class="sxs-lookup"><span data-stu-id="1bfdb-144">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="1bfdb-145">Kopiera ZIP-paketet till enheten</span><span class="sxs-lookup"><span data-stu-id="1bfdb-145">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="1bfdb-146">Anslut till enheten och Expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="1bfdb-146">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="1bfdb-147">Konfigurera fjärr kommunikation till PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="1bfdb-147">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="1bfdb-148">Anslut till PowerShell Core 6-slutpunkt på enhet</span><span class="sxs-lookup"><span data-stu-id="1bfdb-148">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="1bfdb-149">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="1bfdb-149">Deploying on Nano Server</span></span>

<span data-ttu-id="1bfdb-150">Dessa instruktioner förutsätter att en version av PowerShell redan körs på Nano Server-avbildningen och att den har genererats av [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="1bfdb-150">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="1bfdb-151">Nano Server är ett "" "konsol löst" operativ system.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-151">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="1bfdb-152">Kärn binärfiler kan distribueras med två olika metoder.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-152">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="1bfdb-153">Offline – montera den virtuella hård disken för Nano Server och zippa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-153">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="1bfdb-154">Överför zip-filen via en PowerShell-session online och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-154">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="1bfdb-155">I båda fallen behöver du paketet Windows 10 x64 ZIP release och måste köra kommandona i en "administratör" PowerShell-instans.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-155">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="1bfdb-156">Offline-distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="1bfdb-156">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="1bfdb-157">Använd ditt favorit-zip-verktyg för att packa upp paketet till en katalog i den monterade Nano Server-avbildningen.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-157">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="1bfdb-158">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-158">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="1bfdb-159">Anslut till inkorg-instansen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-159">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="1bfdb-160">Följ instruktionerna för att skapa en fjärran sluten slut punkt med hjälp av ["en annan instans teknik"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="1bfdb-160">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="1bfdb-161">Online-distribution av PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="1bfdb-161">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="1bfdb-162">Följande steg vägleder dig genom distributionen av PowerShell Core till en aktiv instans av Nano Server och konfigurationen av dess fjärrslutpunkt.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-162">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="1bfdb-163">Anslut till inkorg-instansen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bfdb-163">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="1bfdb-164">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="1bfdb-164">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="1bfdb-165">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="1bfdb-165">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="1bfdb-166">Extrahera ZIP-filen</span><span class="sxs-lookup"><span data-stu-id="1bfdb-166">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="1bfdb-167">Om du vill använda WSMan-baserad fjärr kommunikation följer du anvisningarna för att skapa en slut punkt för fjärr kommunikation med hjälp av ["en annan instans teknik"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="1bfdb-167">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="1bfdb-168">Så här skapar du en fjärran sluten slut punkt</span><span class="sxs-lookup"><span data-stu-id="1bfdb-168">How to create a remoting endpoint</span></span>

<span data-ttu-id="1bfdb-169">PowerShell Core stöder PowerShell Remoting-protokollet (PSRP) via både WSMan och SSH.</span><span class="sxs-lookup"><span data-stu-id="1bfdb-169">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="1bfdb-170">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="1bfdb-170">For more information, see:</span></span>

- <span data-ttu-id="1bfdb-171">[SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="1bfdb-171">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="1bfdb-172">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="1bfdb-172">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
