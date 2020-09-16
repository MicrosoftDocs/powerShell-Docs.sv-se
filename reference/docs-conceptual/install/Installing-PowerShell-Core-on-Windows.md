---
title: Installera PowerShell i Windows
description: Information om hur du installerar PowerShell på Windows
ms.date: 09/14/2020
ms.openlocfilehash: 8f1b60ef6bfef5c2434b0affabb5e0e7af392b96
ms.sourcegitcommit: 30c0c1563f8e840f24b65297e907f3583d90e677
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90574461"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="848f5-103">Installera PowerShell i Windows</span><span class="sxs-lookup"><span data-stu-id="848f5-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="848f5-104">Det finns flera sätt att installera PowerShell i Windows.</span><span class="sxs-lookup"><span data-stu-id="848f5-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="848f5-105">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="848f5-105">Prerequisites</span></span>

<span data-ttu-id="848f5-106">Den senaste versionen av PowerShell stöds på Windows 7 SP1, Server 2008 R2 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="848f5-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="848f5-107">Om du vill aktivera PowerShell-fjärrkommunikation över WSMan måste följande krav vara uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="848f5-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="848f5-108">Installera [Universal C runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner predating Windows 10.</span><span class="sxs-lookup"><span data-stu-id="848f5-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="848f5-109">Den är tillgänglig via direkt hämtning eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="848f5-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="848f5-110">Fullständigt installerade system har redan det här paketet installerat.</span><span class="sxs-lookup"><span data-stu-id="848f5-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="848f5-111">Installera Windows Management Framework (WMF) 4,0 eller senare på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="848f5-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="848f5-112">Mer information om WMF finns i [Översikt över WMF](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="848f5-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="848f5-113">Ladda ned installations paketet</span><span class="sxs-lookup"><span data-stu-id="848f5-113">Download the installer package</span></span>

<span data-ttu-id="848f5-114">Installera PowerShell på Windows genom att ladda ned installations paketet från vår GitHub- [releases][releases] -sida.</span><span class="sxs-lookup"><span data-stu-id="848f5-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="848f5-115">Rulla ned till **till gångar** -avsnittet på sidan version.</span><span class="sxs-lookup"><span data-stu-id="848f5-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="848f5-116">Avsnittet **till gångar** kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="848f5-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="848f5-117"><a id="msi" />Installera MSI-paketet</span><span class="sxs-lookup"><span data-stu-id="848f5-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="848f5-118">MSI-filen ser ut så här `PowerShell-<version>-win-<os-arch>.msi` .</span><span class="sxs-lookup"><span data-stu-id="848f5-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="848f5-119">Exempel:</span><span class="sxs-lookup"><span data-stu-id="848f5-119">For example:</span></span>

- `PowerShell-7.0.3-win-x64.msi`
- `PowerShell-7.0.3-win-x86.msi`

<span data-ttu-id="848f5-120">När du har laddat ned dubbelklickar du på installations programmet och följer anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="848f5-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="848f5-121">Installations programmet skapar en genväg på Start-menyn i Windows.</span><span class="sxs-lookup"><span data-stu-id="848f5-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="848f5-122">Som standard installeras paketet på `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="848f5-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="848f5-123">Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="848f5-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="848f5-124">PowerShell 7 installeras i en ny katalog och körs sida vid sida med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="848f5-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="848f5-125">För PowerShell Core 6. x är PowerShell 7 en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="848f5-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="848f5-126">PowerShell 7 installeras för att `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="848f5-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="848f5-127">`$env:ProgramFiles\PowerShell\7`Mappen läggs till`$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="848f5-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="848f5-128">`$env:ProgramFiles\PowerShell\6`Mappen tas bort</span><span class="sxs-lookup"><span data-stu-id="848f5-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="848f5-129">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av [zip-installations](#zip) metoden.</span><span class="sxs-lookup"><span data-stu-id="848f5-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="848f5-130">Administrativ installation från kommando raden</span><span class="sxs-lookup"><span data-stu-id="848f5-130">Administrative install from the command line</span></span>

<span data-ttu-id="848f5-131">MSI-paket kan installeras från kommando raden och gör det möjligt för administratörer att distribuera paket utan användar interaktion.</span><span class="sxs-lookup"><span data-stu-id="848f5-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="848f5-132">MSI-paketet innehåller följande egenskaper för att kontrol lera installations alternativen:</span><span class="sxs-lookup"><span data-stu-id="848f5-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="848f5-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – den här egenskapen styr alternativet för att lägga till det **Öppna PowerShell** -objektet i snabb menyn i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="848f5-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="848f5-134">**ENABLE_PSREMOTING** – den här egenskapen styr alternativet för att aktivera PowerShell-fjärrkommunikation under installationen.</span><span class="sxs-lookup"><span data-stu-id="848f5-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="848f5-135">**REGISTER_MANIFEST** – den här egenskapen styr alternativet för registrering av Windows händelse loggnings manifestet.</span><span class="sxs-lookup"><span data-stu-id="848f5-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="848f5-136">I följande exempel visas hur du tyst installerar PowerShell med alla installations alternativ aktiverade.</span><span class="sxs-lookup"><span data-stu-id="848f5-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="848f5-137">En fullständig lista över kommando rads alternativ för `Msiexec.exe` finns i [kommando rads alternativ](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="848f5-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

### <a name="registry-keys-created-during-installation"></a><span data-ttu-id="848f5-138">Register nycklar som skapas under installationen</span><span class="sxs-lookup"><span data-stu-id="848f5-138">Registry keys created during installation</span></span>

<span data-ttu-id="848f5-139">Från och med PowerShell 7,1 skapar MSI-paketet register nycklar som lagrar installations platsen och versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="848f5-139">Beginning in PowerShell 7.1, the MSI package creates registry keys that store the installation location and version of PowerShell.</span></span> <span data-ttu-id="848f5-140">Dessa värden finns i `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` .</span><span class="sxs-lookup"><span data-stu-id="848f5-140">These values are located in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`.</span></span> <span data-ttu-id="848f5-141">Värdet för `<GUID>` är unikt för varje build-typ (version eller förhands granskning), huvud version och arkitektur.</span><span class="sxs-lookup"><span data-stu-id="848f5-141">The value of `<GUID>` is unique for each build type (release or preview), major version, and architecture.</span></span>

|    <span data-ttu-id="848f5-142">Frisläpp</span><span class="sxs-lookup"><span data-stu-id="848f5-142">Release</span></span>    | <span data-ttu-id="848f5-143">Arkitektur</span><span class="sxs-lookup"><span data-stu-id="848f5-143">Architecture</span></span> |                                          <span data-ttu-id="848f5-144">Registernyckel</span><span class="sxs-lookup"><span data-stu-id="848f5-144">Registry Key</span></span>                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| <span data-ttu-id="848f5-145">7.1. x-version</span><span class="sxs-lookup"><span data-stu-id="848f5-145">7.1.x Release</span></span> |     <span data-ttu-id="848f5-146">x86</span><span class="sxs-lookup"><span data-stu-id="848f5-146">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| <span data-ttu-id="848f5-147">7.1. x-version</span><span class="sxs-lookup"><span data-stu-id="848f5-147">7.1.x Release</span></span> |     <span data-ttu-id="848f5-148">x64</span><span class="sxs-lookup"><span data-stu-id="848f5-148">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| <span data-ttu-id="848f5-149">7.1. x-förhandsgranskning</span><span class="sxs-lookup"><span data-stu-id="848f5-149">7.1.x Preview</span></span> |     <span data-ttu-id="848f5-150">x86</span><span class="sxs-lookup"><span data-stu-id="848f5-150">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| <span data-ttu-id="848f5-151">7.1. x-förhandsgranskning</span><span class="sxs-lookup"><span data-stu-id="848f5-151">7.1.x Preview</span></span> |     <span data-ttu-id="848f5-152">x64</span><span class="sxs-lookup"><span data-stu-id="848f5-152">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

<span data-ttu-id="848f5-153">Detta kan användas av administratörer och utvecklare för att hitta sökvägen till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="848f5-153">This can be used by administrators and developers to find the path to PowerShell.</span></span> <span data-ttu-id="848f5-154">`<GUID>`Värdena är desamma för alla för hands versioner och del versioner.</span><span class="sxs-lookup"><span data-stu-id="848f5-154">The `<GUID>` values will be the same for all preview and minor version releases.</span></span> <span data-ttu-id="848f5-155">`<GUID>`Värdena ändras för varje större version.</span><span class="sxs-lookup"><span data-stu-id="848f5-155">The `<GUID>` values are changed for each major release.</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="848f5-156"><a id="msix" />Installera MSIX-paketet</span><span class="sxs-lookup"><span data-stu-id="848f5-156"><a id="msix" />Installing the MSIX package</span></span>

> [!NOTE]
> <span data-ttu-id="848f5-157">MSIX-paketet stöds inte officiellt för tillfället.</span><span class="sxs-lookup"><span data-stu-id="848f5-157">The MSIX package is not officially supported at this time.</span></span> <span data-ttu-id="848f5-158">Vi fortsätter att bygga paketet enbart för internt test ändamål.</span><span class="sxs-lookup"><span data-stu-id="848f5-158">We continue to build the package for internal testing purposes only.</span></span>

<span data-ttu-id="848f5-159">Om du vill installera MSIX-paketet manuellt på en Windows 10-klient laddar du ned MSIX-paketet från vår GitHub [releases][releases] -sida.</span><span class="sxs-lookup"><span data-stu-id="848f5-159">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="848f5-160">Rulla ned till **till gångar** -avsnittet i den version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="848f5-160">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="848f5-161">Avsnittet till gångar kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="848f5-161">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="848f5-162">MSIX-filen ser ut så här – `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="848f5-162">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="848f5-163">Du måste använda cmdleten för att installera paketet `Add-AppxPackage` .</span><span class="sxs-lookup"><span data-stu-id="848f5-163">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="installing-the-zip-package"></a><span data-ttu-id="848f5-164"><a id="zip" />Installera ZIP-paketet</span><span class="sxs-lookup"><span data-stu-id="848f5-164"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="848f5-165">Det finns PowerShell-Arkiv för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="848f5-165">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="848f5-166">Installation av ZIP-arkivet kontrollerar inte kraven som MSI-paketen gör.</span><span class="sxs-lookup"><span data-stu-id="848f5-166">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="848f5-167">Hämta ZIP-arkivet från sidan [versioner][releases] .</span><span class="sxs-lookup"><span data-stu-id="848f5-167">Download the ZIP archive from the [releases][releases] page.</span></span> <span data-ttu-id="848f5-168">Beroende på hur du laddar ned filen kan du behöva avblockera filen med hjälp av `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="848f5-168">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="848f5-169">Zippa upp innehållet till valfri plats och kör `pwsh.exe` därifrån.</span><span class="sxs-lookup"><span data-stu-id="848f5-169">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="848f5-170">Se till att du uppfyller [kraven](#prerequisites)för fjärr kommunikation över WSMan för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="848f5-170">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="848f5-171">Distribuera i Windows 10 IoT Enterprise</span><span class="sxs-lookup"><span data-stu-id="848f5-171">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="848f5-172">Windows 10 IoT Enterprise levereras med Windows PowerShell, som vi kan använda för att distribuera PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="848f5-172">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="848f5-173">Skapa `PSSession` till mål enhet</span><span class="sxs-lookup"><span data-stu-id="848f5-173">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. <span data-ttu-id="848f5-174">Kopiera ZIP-paketet till enheten</span><span class="sxs-lookup"><span data-stu-id="848f5-174">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. <span data-ttu-id="848f5-175">Anslut till enheten och Expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="848f5-175">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. <span data-ttu-id="848f5-176">Konfigurera fjärr kommunikation till PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="848f5-176">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

1. <span data-ttu-id="848f5-177">Anslut till PowerShell 7-slutpunkt på enhet</span><span class="sxs-lookup"><span data-stu-id="848f5-177">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="848f5-178">Distribuera på Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="848f5-178">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="848f5-179">Windows 10 IoT Core lägger till Windows PowerShell när du inkluderar *IOT_POWERSHELL* funktion som vi kan använda för att distribuera PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="848f5-179">Windows 10 IoT Core adds Windows PowerShell when you include *IOT_POWERSHELL* feature, which we can use to deploy PowerShell 7.</span></span>
<span data-ttu-id="848f5-180">Stegen som definieras ovan för Windows 10 IoT Enterprise kan också följas av IoT Core.</span><span class="sxs-lookup"><span data-stu-id="848f5-180">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="848f5-181">För att lägga till den senaste PowerShell-versionen i leverans avbildningen använder du kommandot [import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) för att inkludera paketet i workarea och lägga till *OPENSRC_POWERSHELL* funktion i avbildningen.</span><span class="sxs-lookup"><span data-stu-id="848f5-181">For adding the latest powershell in the shipping image, use [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) command to include the package in the workarea and add *OPENSRC_POWERSHELL* feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="848f5-182">Windows PowerShell läggs inte till i ARM64-arkitekturen när du tar med *IOT_POWERSHELL*.</span><span class="sxs-lookup"><span data-stu-id="848f5-182">For ARM64 architecture, Windows Powershell is not added when you include *IOT_POWERSHELL*.</span></span> <span data-ttu-id="848f5-183">Det innebär att zip-baserad installation inte fungerar.</span><span class="sxs-lookup"><span data-stu-id="848f5-183">So the zip based install will not work.</span></span>
> <span data-ttu-id="848f5-184">Du måste använda kommandot Import-PSCoreRelease för att lägga till det i avbildningen.</span><span class="sxs-lookup"><span data-stu-id="848f5-184">You will need to use Import-PSCoreRelease command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="848f5-185">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="848f5-185">Deploying on Nano Server</span></span>

<span data-ttu-id="848f5-186">Dessa instruktioner förutsätter att Nano-servern är ett "" "" "-"-OS som har en version av PowerShell som redan körs på den.</span><span class="sxs-lookup"><span data-stu-id="848f5-186">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="848f5-187">Mer information finns i dokumentationen för [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) .</span><span class="sxs-lookup"><span data-stu-id="848f5-187">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="848f5-188">PowerShell-binärfiler kan distribueras med två olika metoder.</span><span class="sxs-lookup"><span data-stu-id="848f5-188">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="848f5-189">Offline – montera den virtuella hård disken för Nano Server och zippa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="848f5-189">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="848f5-190">Överför zip-filen via en PowerShell-session online och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="848f5-190">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="848f5-191">I båda fallen behöver du paketet Windows 10 x64 ZIP release.</span><span class="sxs-lookup"><span data-stu-id="848f5-191">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="848f5-192">Kör kommandona i en "administratör"-instans av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="848f5-192">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="848f5-193">Offline-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="848f5-193">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="848f5-194">Använd ditt favorit-zip-verktyg för att packa upp paketet till en katalog i den monterade Nano Server-avbildningen.</span><span class="sxs-lookup"><span data-stu-id="848f5-194">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="848f5-195">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="848f5-195">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="848f5-196">Anslut till den inbyggda instansen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="848f5-196">Connect to the built-in instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="848f5-197">Följ instruktionerna för att skapa en fjärran sluten slut punkt med hjälp av ["en annan instans teknik"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="848f5-197">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="848f5-198">Online-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="848f5-198">Online Deployment of PowerShell</span></span>

<span data-ttu-id="848f5-199">Distribuera PowerShell till Nano Server med hjälp av följande steg.</span><span class="sxs-lookup"><span data-stu-id="848f5-199">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="848f5-200">Ansluta till den inbyggda instansen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="848f5-200">Connect to the built-in instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="848f5-201">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="848f5-201">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="848f5-202">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="848f5-202">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="848f5-203">Extrahera ZIP-filen</span><span class="sxs-lookup"><span data-stu-id="848f5-203">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="848f5-204">Om du vill använda WSMan-baserad fjärr kommunikation följer du anvisningarna för att skapa en slut punkt för fjärr kommunikation med hjälp av ["en annan instans teknik"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="848f5-204">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="848f5-205">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="848f5-205">Install as a .NET Global tool</span></span>

<span data-ttu-id="848f5-206">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="848f5-206">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="848f5-207">Installations programmet för dotNET-verktyget lägger till `$env:USERPROFILE\dotnet\tools` i din `$env:PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="848f5-207">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="848f5-208">Men det gränssnitt som körs har inte uppdaterats `$env:PATH` .</span><span class="sxs-lookup"><span data-stu-id="848f5-208">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="848f5-209">Du kan starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="848f5-209">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="install-powershell-via-winget"></a><span data-ttu-id="848f5-210">Installera PowerShell via Winget</span><span class="sxs-lookup"><span data-stu-id="848f5-210">Install PowerShell via Winget</span></span>

<span data-ttu-id="848f5-211">Med `winget` kommando rads verktyget kan utvecklare identifiera, installera, uppgradera, ta bort och konfigurera program på Windows 10-datorer.</span><span class="sxs-lookup"><span data-stu-id="848f5-211">The `winget` command-line tool enables developers to discover, install, upgrade, remove and configure applications on Windows 10 computers.</span></span> <span data-ttu-id="848f5-212">Det här verktyget är klient gränssnittet för Windows Package Manager-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="848f5-212">This tool is the client interface to the Windows Package Manager service.</span></span>

> [!NOTE]
> <span data-ttu-id="848f5-213">`winget`Verktyget är för närvarande en för hands version.</span><span class="sxs-lookup"><span data-stu-id="848f5-213">The `winget` tool is currently a preview.</span></span> <span data-ttu-id="848f5-214">Alla planerade funktioner är inte tillgängliga för tillfället.</span><span class="sxs-lookup"><span data-stu-id="848f5-214">Not all planned functionality is available at this time.</span></span>
> <span data-ttu-id="848f5-215">Verktygets alternativ och funktioner kan komma att ändras.</span><span class="sxs-lookup"><span data-stu-id="848f5-215">The tool's options and features are subject to change.</span></span> <span data-ttu-id="848f5-216">Du bör inte använda den här metoden i ett scenario för produktions distribution.</span><span class="sxs-lookup"><span data-stu-id="848f5-216">You should not use this method in a production deployment scenario.</span></span> <span data-ttu-id="848f5-217">I [Winget] -dokumentationen finns en lista över system krav och installations anvisningar.</span><span class="sxs-lookup"><span data-stu-id="848f5-217">See the [winget] documentation for a list of system requirements and install instructions.</span></span>

<span data-ttu-id="848f5-218">Följande kommandon kan användas för att installera PowerShell med de publicerade `winget` paketen:</span><span class="sxs-lookup"><span data-stu-id="848f5-218">The following commands can be used to install PowerShell using the published `winget` packages:</span></span>

1. <span data-ttu-id="848f5-219">Sök efter den senaste versionen av PowerShell</span><span class="sxs-lookup"><span data-stu-id="848f5-219">Search for the latest version of PowerShell</span></span>

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.0.3
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.0-preview.5
   ```

1. <span data-ttu-id="848f5-220">Installera en version av PowerShell med `--exact` parametern</span><span class="sxs-lookup"><span data-stu-id="848f5-220">Install a version of PowerShell using the `--exact` parameter</span></span>

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="848f5-221">Så här skapar du en fjärran sluten slut punkt</span><span class="sxs-lookup"><span data-stu-id="848f5-221">How to create a remoting endpoint</span></span>

<span data-ttu-id="848f5-222">PowerShell stöder PowerShell Remoting-protokollet (PSRP) via både WSMan och SSH.</span><span class="sxs-lookup"><span data-stu-id="848f5-222">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="848f5-223">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="848f5-223">For more information, see:</span></span>

- <span data-ttu-id="848f5-224">[SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="848f5-224">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="848f5-225">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="848f5-225">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="installation-support"></a><span data-ttu-id="848f5-226">Installations stöd</span><span class="sxs-lookup"><span data-stu-id="848f5-226">Installation support</span></span>

<span data-ttu-id="848f5-227">Microsoft stöder installations metoderna i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="848f5-227">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="848f5-228">Det kan finnas andra installations metoder som är tillgängliga från andra källor.</span><span class="sxs-lookup"><span data-stu-id="848f5-228">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="848f5-229">Dessa verktyg och metoder kan fungera, men Microsoft stöder inte dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="848f5-229">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
