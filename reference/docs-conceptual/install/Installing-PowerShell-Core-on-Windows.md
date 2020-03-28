---
title: Installera PowerShell i Windows
description: Information om hur du installerar PowerShell på Windows
ms.date: 08/06/2018
ms.openlocfilehash: ea5432725f4baea8c688fb8e67482910e2c3981e
ms.sourcegitcommit: b6cf10224eb9f32919a505cdffbe5968241c18a1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/28/2020
ms.locfileid: "80374883"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="4badb-103">Installera PowerShell i Windows</span><span class="sxs-lookup"><span data-stu-id="4badb-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="4badb-104">Det finns flera sätt att installera PowerShell i Windows.</span><span class="sxs-lookup"><span data-stu-id="4badb-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4badb-105">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="4badb-105">Prerequisites</span></span>

<span data-ttu-id="4badb-106">Den senaste versionen av PowerShell stöds på Windows 7 SP1, Server 2008 R2 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="4badb-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="4badb-107">Om du vill aktivera PowerShell-fjärrkommunikation över WSMan måste följande krav vara uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="4badb-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="4badb-108">Installera [Universal C runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner predating Windows 10.</span><span class="sxs-lookup"><span data-stu-id="4badb-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="4badb-109">Den är tillgänglig via direkt hämtning eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="4badb-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="4badb-110">Fullständigt installerade system har redan det här paketet installerat.</span><span class="sxs-lookup"><span data-stu-id="4badb-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="4badb-111">Installera Windows Management Framework (WMF) 4,0 eller senare på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="4badb-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="4badb-112">Mer information om WMF finns i [Översikt över WMF](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="4badb-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="4badb-113">Ladda ned installations paketet</span><span class="sxs-lookup"><span data-stu-id="4badb-113">Download the installer package</span></span>

<span data-ttu-id="4badb-114">Installera PowerShell på Windows genom att ladda ned installations paketet från vår GitHub- [releases][releases] -sida.</span><span class="sxs-lookup"><span data-stu-id="4badb-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="4badb-115">Rulla ned till **till gångar** -avsnittet på sidan version.</span><span class="sxs-lookup"><span data-stu-id="4badb-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="4badb-116">Avsnittet **till gångar** kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="4badb-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="4badb-117"><a id="msi" />installera MSI-paketet</span><span class="sxs-lookup"><span data-stu-id="4badb-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="4badb-118">MSI-filen ser ut som `PowerShell-<version>-win-<os-arch>.msi`.</span><span class="sxs-lookup"><span data-stu-id="4badb-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="4badb-119">Några exempel:</span><span class="sxs-lookup"><span data-stu-id="4badb-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="4badb-120">När du har laddat ned dubbelklickar du på installations programmet och följer anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="4badb-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="4badb-121">Installations programmet skapar en genväg på Start-menyn i Windows.</span><span class="sxs-lookup"><span data-stu-id="4badb-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="4badb-122">Som standard installeras paketet på `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="4badb-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="4badb-123">Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="4badb-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="4badb-124">PowerShell 7 installeras i en ny katalog och körs sida vid sida med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="4badb-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="4badb-125">För PowerShell Core 6. x är PowerShell 7 en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="4badb-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="4badb-126">PowerShell 7 installeras för att `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="4badb-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="4badb-127">Mappen `$env:ProgramFiles\PowerShell\7` läggs till i `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="4badb-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="4badb-128">Mappen `$env:ProgramFiles\PowerShell\6` tas bort</span><span class="sxs-lookup"><span data-stu-id="4badb-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="4badb-129">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av [zip-installations](#zip) metoden.</span><span class="sxs-lookup"><span data-stu-id="4badb-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="4badb-130">Administrativ installation från kommando raden</span><span class="sxs-lookup"><span data-stu-id="4badb-130">Administrative install from the command line</span></span>

<span data-ttu-id="4badb-131">MSI-paket kan installeras från kommando raden och gör det möjligt för administratörer att distribuera paket utan användar interaktion.</span><span class="sxs-lookup"><span data-stu-id="4badb-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="4badb-132">MSI-paketet innehåller följande egenskaper för att kontrol lera installations alternativen:</span><span class="sxs-lookup"><span data-stu-id="4badb-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="4badb-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – den här egenskapen styr alternativet för att lägga till det **Öppna PowerShell** -objektet i snabb menyn i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="4badb-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="4badb-134">**ENABLE_PSREMOTING** – den här egenskapen styr alternativet för att aktivera PowerShell-fjärrkommunikation under installationen.</span><span class="sxs-lookup"><span data-stu-id="4badb-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="4badb-135">**REGISTER_MANIFEST** – den här egenskapen styr alternativet för registrering av Windows händelse loggnings manifestet.</span><span class="sxs-lookup"><span data-stu-id="4badb-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="4badb-136">I följande exempel visas hur du tyst installerar PowerShell med alla installations alternativ aktiverade.</span><span class="sxs-lookup"><span data-stu-id="4badb-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="4badb-137">En fullständig lista över kommando rads alternativ för `Msiexec.exe`finns i [kommando rads alternativ](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="4badb-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="4badb-138"><a id="msix" />installera MSIX-paketet</span><span class="sxs-lookup"><span data-stu-id="4badb-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="4badb-139">Om du vill installera MSIX-paketet manuellt på en Windows 10-klient laddar du ned MSIX-paketet från vår GitHub [releases][releases] -sida.</span><span class="sxs-lookup"><span data-stu-id="4badb-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="4badb-140">Rulla ned till **till gångar** -avsnittet i den version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="4badb-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="4badb-141">Avsnittet till gångar kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="4badb-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="4badb-142">MSIX-filen ser ut så här – `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="4badb-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="4badb-143">Du måste använda `Add-AppxPackage`-cmdleten för att installera paketet.</span><span class="sxs-lookup"><span data-stu-id="4badb-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="4badb-144">MSIX-paketet har ännu inte släppts.</span><span class="sxs-lookup"><span data-stu-id="4badb-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="4badb-145">När paketet har släppts är paketet tillgängligt i Microsoft Store och från sidan GitHub- [versioner][releases] .</span><span class="sxs-lookup"><span data-stu-id="4badb-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="4badb-146"><a id="zip" />installation av ZIP-paketet</span><span class="sxs-lookup"><span data-stu-id="4badb-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="4badb-147">Det finns PowerShell-Arkiv för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="4badb-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="4badb-148">Installation av ZIP-arkivet kontrollerar inte kraven som MSI-paketen gör.</span><span class="sxs-lookup"><span data-stu-id="4badb-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="4badb-149">Se till att du uppfyller [kraven](#prerequisites)för fjärr kommunikation över WSMan för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="4badb-149">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="4badb-150">Distribuera på Windows IoT</span><span class="sxs-lookup"><span data-stu-id="4badb-150">Deploying on Windows IoT</span></span>

<span data-ttu-id="4badb-151">Windows IoT levereras med Windows PowerShell, som vi kan använda för att distribuera PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="4badb-151">Windows IoT comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="4badb-152">Skapa `PSSession` till mål enhet</span><span class="sxs-lookup"><span data-stu-id="4badb-152">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="4badb-153">Kopiera ZIP-paketet till enheten</span><span class="sxs-lookup"><span data-stu-id="4badb-153">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="4badb-154">Anslut till enheten och Expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="4badb-154">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="4badb-155">Konfigurera fjärr kommunikation till PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="4badb-155">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="4badb-156">Anslut till PowerShell 7-slutpunkt på enhet</span><span class="sxs-lookup"><span data-stu-id="4badb-156">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="4badb-157">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="4badb-157">Deploying on Nano Server</span></span>

<span data-ttu-id="4badb-158">Dessa instruktioner förutsätter att Nano-servern är ett "" "" "-"-OS som har en version av PowerShell som redan körs på den.</span><span class="sxs-lookup"><span data-stu-id="4badb-158">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="4badb-159">Mer information finns i dokumentationen för [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) .</span><span class="sxs-lookup"><span data-stu-id="4badb-159">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="4badb-160">PowerShell-binärfiler kan distribueras med två olika metoder.</span><span class="sxs-lookup"><span data-stu-id="4badb-160">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="4badb-161">Offline – montera den virtuella hård disken för Nano Server och zippa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="4badb-161">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="4badb-162">Överför zip-filen via en PowerShell-session online och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="4badb-162">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="4badb-163">I båda fallen behöver du paketet Windows 10 x64 ZIP release.</span><span class="sxs-lookup"><span data-stu-id="4badb-163">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="4badb-164">Kör kommandona i en "administratör"-instans av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4badb-164">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="4badb-165">Offline-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="4badb-165">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="4badb-166">Använd ditt favorit-zip-verktyg för att packa upp paketet till en katalog i den monterade Nano Server-avbildningen.</span><span class="sxs-lookup"><span data-stu-id="4badb-166">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="4badb-167">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="4badb-167">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="4badb-168">Anslut till inkorg-instansen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4badb-168">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="4badb-169">Följ instruktionerna för att skapa en fjärran sluten slut punkt med hjälp av ["en annan instans teknik"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="4badb-169">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="4badb-170">Online-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="4badb-170">Online Deployment of PowerShell</span></span>

<span data-ttu-id="4badb-171">Distribuera PowerShell till Nano Server med hjälp av följande steg.</span><span class="sxs-lookup"><span data-stu-id="4badb-171">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="4badb-172">Anslut till inkorg-instansen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4badb-172">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="4badb-173">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="4badb-173">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="4badb-174">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="4badb-174">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="4badb-175">Extrahera ZIP-filen</span><span class="sxs-lookup"><span data-stu-id="4badb-175">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="4badb-176">Om du vill använda WSMan-baserad fjärr kommunikation följer du anvisningarna för att skapa en slut punkt för fjärr kommunikation med hjälp av ["en annan instans teknik"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="4badb-176">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="4badb-177">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="4badb-177">Install as a .NET Global tool</span></span>

<span data-ttu-id="4badb-178">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="4badb-178">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="4badb-179">Installations programmet för dotNET-verktyget lägger till `$env:USERPROFILE\dotnet\tools` i din `$env:PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="4badb-179">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="4badb-180">Men det gränssnitt som körs har inte den uppdaterade `$env:PATH`.</span><span class="sxs-lookup"><span data-stu-id="4badb-180">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="4badb-181">Du kan starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="4badb-181">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="4badb-182">Så här skapar du en fjärran sluten slut punkt</span><span class="sxs-lookup"><span data-stu-id="4badb-182">How to create a remoting endpoint</span></span>

<span data-ttu-id="4badb-183">PowerShell stöder PowerShell Remoting-protokollet (PSRP) via både WSMan och SSH.</span><span class="sxs-lookup"><span data-stu-id="4badb-183">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="4badb-184">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="4badb-184">For more information, see:</span></span>

- <span data-ttu-id="4badb-185">[SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="4badb-185">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="4badb-186">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="4badb-186">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
