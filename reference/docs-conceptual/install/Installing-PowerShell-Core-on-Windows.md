---
title: Installera PowerShell i Windows
description: Information om hur du installerar PowerShell på Windows
ms.date: 02/02/2021
ms.openlocfilehash: befc5ff156cb7c3843d89e394e903778682ba28e
ms.sourcegitcommit: 40b6d8e9b6d791ac69e2ff85224e900b21552bc1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2021
ms.locfileid: "99536498"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="c64fe-103">Installera PowerShell i Windows</span><span class="sxs-lookup"><span data-stu-id="c64fe-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="c64fe-104">Det finns flera sätt att installera PowerShell i Windows.</span><span class="sxs-lookup"><span data-stu-id="c64fe-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c64fe-105">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="c64fe-105">Prerequisites</span></span>

<span data-ttu-id="c64fe-106">Den senaste versionen av PowerShell stöds på Windows 7 SP1, Server 2008 R2 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="c64fe-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="c64fe-107">Om du vill aktivera PowerShell-fjärrkommunikation över WSMan måste följande krav vara uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="c64fe-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="c64fe-108">Installera [Universal C runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner predating Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c64fe-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="c64fe-109">Den är tillgänglig via direkt hämtning eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="c64fe-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="c64fe-110">Fullständigt installerade system har redan det här paketet installerat.</span><span class="sxs-lookup"><span data-stu-id="c64fe-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="c64fe-111">Installera Windows Management Framework (WMF) 4,0 eller senare på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="c64fe-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="c64fe-112">Mer information om WMF finns i [Översikt över WMF](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="c64fe-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="c64fe-113">Ladda ned installations paketet</span><span class="sxs-lookup"><span data-stu-id="c64fe-113">Download the installer package</span></span>

<span data-ttu-id="c64fe-114">Om du vill installera PowerShell på Windows laddar du ned det [senaste][] installations paketet från GitHub.</span><span class="sxs-lookup"><span data-stu-id="c64fe-114">To install PowerShell on Windows, download the [latest][] install package from GitHub.</span></span> <span data-ttu-id="c64fe-115">Du kan också hitta den senaste för [hands][] versionen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-115">You can also find the latest [preview][] version.</span></span> <span data-ttu-id="c64fe-116">Rulla ned till **till gångar** -avsnittet på sidan version.</span><span class="sxs-lookup"><span data-stu-id="c64fe-116">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="c64fe-117">Avsnittet **till gångar** kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="c64fe-117">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="c64fe-118"><a id="msi" />Installera MSI-paketet</span><span class="sxs-lookup"><span data-stu-id="c64fe-118"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="c64fe-119">MSI-filen ser ut så här `PowerShell-<version>-win-<os-arch>.msi` .</span><span class="sxs-lookup"><span data-stu-id="c64fe-119">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="c64fe-120">Exempel:</span><span class="sxs-lookup"><span data-stu-id="c64fe-120">For example:</span></span>

- `PowerShell-7.1.1-win-x64.msi`
- `PowerShell-7.1.1-win-x86.msi`

<span data-ttu-id="c64fe-121">När du har laddat ned dubbelklickar du på installations programmet och följer anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="c64fe-121">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="c64fe-122">Installations programmet skapar en genväg på Start-menyn i Windows.</span><span class="sxs-lookup"><span data-stu-id="c64fe-122">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="c64fe-123">Som standard installeras paketet på `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="c64fe-123">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="c64fe-124">Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="c64fe-124">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="c64fe-125">PowerShell 7,1 installeras i en ny katalog och körs sida vid sida med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="c64fe-125">PowerShell 7.1 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span>
> <span data-ttu-id="c64fe-126">PowerShell 7,1 är en uppgradering på plats som ersätter PowerShell 6. x.</span><span class="sxs-lookup"><span data-stu-id="c64fe-126">PowerShell 7.1 is an in-place upgrade that replaces PowerShell 6.x.</span></span> <span data-ttu-id="c64fe-127">eller PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="c64fe-127">or PowerShell 7.0.</span></span>
>
> - <span data-ttu-id="c64fe-128">PowerShell 7,1 är installerat på `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="c64fe-128">PowerShell 7.1 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="c64fe-129">`$env:ProgramFiles\PowerShell\7`Mappen läggs till`$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="c64fe-129">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="c64fe-130">`$env:ProgramFiles\PowerShell\6`Mappen tas bort</span><span class="sxs-lookup"><span data-stu-id="c64fe-130">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="c64fe-131">Om du behöver köra PowerShell 7,1 sida vid sida med andra versioner använder du [zip-installations](#zip) metoden för att installera den andra versionen i en annan mapp.</span><span class="sxs-lookup"><span data-stu-id="c64fe-131">If you need to run PowerShell 7.1 side-by-side with other versions, use the [ZIP install](#zip) method to install the other version to a different folder.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="c64fe-132">Administrativ installation från kommando raden</span><span class="sxs-lookup"><span data-stu-id="c64fe-132">Administrative install from the command line</span></span>

<span data-ttu-id="c64fe-133">MSI-paket kan installeras från kommando raden och gör det möjligt för administratörer att distribuera paket utan användar interaktion.</span><span class="sxs-lookup"><span data-stu-id="c64fe-133">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="c64fe-134">MSI-paketet innehåller följande egenskaper för att kontrol lera installations alternativen:</span><span class="sxs-lookup"><span data-stu-id="c64fe-134">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="c64fe-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – den här egenskapen styr alternativet för att lägga till det **Öppna PowerShell** -objektet i snabb menyn i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="c64fe-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="c64fe-136">**ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL** – den här egenskapen styr alternativet för att lägga till kommandot **Kör med PowerShell** på snabb menyn i Utforskaren i Windows.</span><span class="sxs-lookup"><span data-stu-id="c64fe-136">**ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL** - This property controls the option for adding the **Run with PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="c64fe-137">**ENABLE_PSREMOTING** – den här egenskapen styr alternativet för att aktivera PowerShell-fjärrkommunikation under installationen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-137">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="c64fe-138">**REGISTER_MANIFEST** – den här egenskapen styr alternativet för registrering av Windows händelse loggnings manifestet.</span><span class="sxs-lookup"><span data-stu-id="c64fe-138">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="c64fe-139">I följande exempel visas hur du tyst installerar PowerShell med alla installations alternativ aktiverade.</span><span class="sxs-lookup"><span data-stu-id="c64fe-139">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.1.1-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="c64fe-140">En fullständig lista över kommando rads alternativ för `Msiexec.exe` finns i [kommando rads alternativ](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="c64fe-140">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

### <a name="registry-keys-created-during-installation"></a><span data-ttu-id="c64fe-141">Register nycklar som skapas under installationen</span><span class="sxs-lookup"><span data-stu-id="c64fe-141">Registry keys created during installation</span></span>

<span data-ttu-id="c64fe-142">Från och med PowerShell 7,1 skapar MSI-paketet register nycklar som lagrar installations platsen och versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64fe-142">Beginning in PowerShell 7.1, the MSI package creates registry keys that store the installation location and version of PowerShell.</span></span> <span data-ttu-id="c64fe-143">Dessa värden finns i `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` .</span><span class="sxs-lookup"><span data-stu-id="c64fe-143">These values are located in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`.</span></span> <span data-ttu-id="c64fe-144">Värdet för `<GUID>` är unikt för varje build-typ (version eller förhands granskning), huvud version och arkitektur.</span><span class="sxs-lookup"><span data-stu-id="c64fe-144">The value of `<GUID>` is unique for each build type (release or preview), major version, and architecture.</span></span>

|    <span data-ttu-id="c64fe-145">Frisläpp</span><span class="sxs-lookup"><span data-stu-id="c64fe-145">Release</span></span>    | <span data-ttu-id="c64fe-146">Arkitektur</span><span class="sxs-lookup"><span data-stu-id="c64fe-146">Architecture</span></span> |                                          <span data-ttu-id="c64fe-147">Registernyckel</span><span class="sxs-lookup"><span data-stu-id="c64fe-147">Registry Key</span></span>                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c64fe-148">7.1. x-version</span><span class="sxs-lookup"><span data-stu-id="c64fe-148">7.1.x Release</span></span> |     <span data-ttu-id="c64fe-149">x86</span><span class="sxs-lookup"><span data-stu-id="c64fe-149">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| <span data-ttu-id="c64fe-150">7.1. x-version</span><span class="sxs-lookup"><span data-stu-id="c64fe-150">7.1.x Release</span></span> |     <span data-ttu-id="c64fe-151">x64</span><span class="sxs-lookup"><span data-stu-id="c64fe-151">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| <span data-ttu-id="c64fe-152">7.1. x-förhandsgranskning</span><span class="sxs-lookup"><span data-stu-id="c64fe-152">7.1.x Preview</span></span> |     <span data-ttu-id="c64fe-153">x86</span><span class="sxs-lookup"><span data-stu-id="c64fe-153">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| <span data-ttu-id="c64fe-154">7.1. x-förhandsgranskning</span><span class="sxs-lookup"><span data-stu-id="c64fe-154">7.1.x Preview</span></span> |     <span data-ttu-id="c64fe-155">x64</span><span class="sxs-lookup"><span data-stu-id="c64fe-155">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

<span data-ttu-id="c64fe-156">Detta kan användas av administratörer och utvecklare för att hitta sökvägen till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64fe-156">This can be used by administrators and developers to find the path to PowerShell.</span></span> <span data-ttu-id="c64fe-157">`<GUID>`Värdena är desamma för alla för hands versioner och del versioner.</span><span class="sxs-lookup"><span data-stu-id="c64fe-157">The `<GUID>` values will be the same for all preview and minor version releases.</span></span> <span data-ttu-id="c64fe-158">`<GUID>`Värdena ändras för varje större version.</span><span class="sxs-lookup"><span data-stu-id="c64fe-158">The `<GUID>` values are changed for each major release.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="c64fe-159"><a id="zip" />Installera ZIP-paketet</span><span class="sxs-lookup"><span data-stu-id="c64fe-159"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="c64fe-160">Det finns PowerShell-Arkiv för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="c64fe-160">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="c64fe-161">Ladda ned något av följande ZIP-arkiv från sidan [releases] [releases].</span><span class="sxs-lookup"><span data-stu-id="c64fe-161">Download one of the following ZIP archives from the [releases][releases] page.</span></span>

- <span data-ttu-id="c64fe-162">PowerShell-7.1.1-win-x64.zip</span><span class="sxs-lookup"><span data-stu-id="c64fe-162">PowerShell-7.1.1-win-x64.zip</span></span>
- <span data-ttu-id="c64fe-163">PowerShell-7.1.1-win-x86.zip</span><span class="sxs-lookup"><span data-stu-id="c64fe-163">PowerShell-7.1.1-win-x86.zip</span></span>
- <span data-ttu-id="c64fe-164">PowerShell-7.1.1-win-arm64.zip</span><span class="sxs-lookup"><span data-stu-id="c64fe-164">PowerShell-7.1.1-win-arm64.zip</span></span>
- <span data-ttu-id="c64fe-165">PowerShell-7.1.1-win-arm32.zip</span><span class="sxs-lookup"><span data-stu-id="c64fe-165">PowerShell-7.1.1-win-arm32.zip</span></span>

<span data-ttu-id="c64fe-166">Beroende på hur du laddar ned filen kan du behöva avblockera filen med hjälp av `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c64fe-166">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="c64fe-167">Zippa upp innehållet till valfri plats och kör `pwsh.exe` därifrån.</span><span class="sxs-lookup"><span data-stu-id="c64fe-167">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="c64fe-168">Till skillnad från när du installerar MSI-paketen söker inte du efter krav i ZIP-arkivet.</span><span class="sxs-lookup"><span data-stu-id="c64fe-168">Unlike installing the MSI packages, installing the ZIP archive doesn't check for prerequisites.</span></span> <span data-ttu-id="c64fe-169">Se till att du uppfyller [kraven](#prerequisites)för fjärr kommunikation över WSMan för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="c64fe-169">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

<span data-ttu-id="c64fe-170">Använd den här metoden för att installera den ARM-baserade versionen av PowerShell på datorer som Microsoft Surface Pro X. För bästa resultat bör du installera PowerShell i till- `$env:ProgramFiles\PowerShell\7` mappen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-170">Use this method to install the ARM-based version of PowerShell on computers like the Microsoft Surface Pro X. For best results, install PowerShell to the to `$env:ProgramFiles\PowerShell\7` folder.</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="c64fe-171">Distribuera i Windows 10 IoT Enterprise</span><span class="sxs-lookup"><span data-stu-id="c64fe-171">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="c64fe-172">Windows 10 IoT Enterprise levereras med Windows PowerShell, som vi kan använda för att distribuera PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c64fe-172">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="c64fe-173">Skapa `PSSession` till mål enhet</span><span class="sxs-lookup"><span data-stu-id="c64fe-173">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. <span data-ttu-id="c64fe-174">Kopiera ZIP-paketet till enheten</span><span class="sxs-lookup"><span data-stu-id="c64fe-174">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. <span data-ttu-id="c64fe-175">Anslut till enheten och Expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="c64fe-175">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. <span data-ttu-id="c64fe-176">Konfigurera fjärr kommunikation till PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c64fe-176">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. <span data-ttu-id="c64fe-177">Anslut till PowerShell 7-slutpunkt på enhet</span><span class="sxs-lookup"><span data-stu-id="c64fe-177">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="c64fe-178">Distribuera på Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="c64fe-178">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="c64fe-179">Windows 10 IoT Core lägger till Windows PowerShell när du inkluderar _IOT_POWERSHELL_ funktion som vi kan använda för att distribuera PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c64fe-179">Windows 10 IoT Core adds Windows PowerShell when you include _IOT_POWERSHELL_ feature, which we can use to deploy PowerShell 7.</span></span> <span data-ttu-id="c64fe-180">Stegen som definieras ovan för Windows 10 IoT Enterprise kan också följas av IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c64fe-180">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="c64fe-181">För att lägga till den senaste PowerShell-versionen i leverans avbildningen använder du kommandot [import-PSCoreRelease][] för att inkludera paketet i workarea och lägga till _OPENSRC_POWERSHELL_ funktion i avbildningen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-181">For adding the latest PowerShell in the shipping image, use [Import-PSCoreRelease][] command to include the package in the workarea and add _OPENSRC_POWERSHELL_ feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="c64fe-182">Windows PowerShell läggs inte till i ARM64-arkitekturen när du tar med _IOT_POWERSHELL_.</span><span class="sxs-lookup"><span data-stu-id="c64fe-182">For ARM64 architecture, Windows PowerShell is not added when you include _IOT_POWERSHELL_.</span></span> <span data-ttu-id="c64fe-183">Det innebär att zip-baserad installation inte fungerar.</span><span class="sxs-lookup"><span data-stu-id="c64fe-183">So the zip based install will not work.</span></span> <span data-ttu-id="c64fe-184">Du måste använda `Import-PSCoreRelease` kommandot för att lägga till det i avbildningen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-184">You will need to use `Import-PSCoreRelease` command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="c64fe-185">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="c64fe-185">Deploying on Nano Server</span></span>

<span data-ttu-id="c64fe-186">Dessa instruktioner förutsätter att Nano-servern är ett "" "" "-"-OS som har en version av PowerShell som redan körs på den.</span><span class="sxs-lookup"><span data-stu-id="c64fe-186">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="c64fe-187">Mer information finns i dokumentationen för [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) .</span><span class="sxs-lookup"><span data-stu-id="c64fe-187">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="c64fe-188">PowerShell-binärfiler kan distribueras med två olika metoder.</span><span class="sxs-lookup"><span data-stu-id="c64fe-188">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="c64fe-189">Offline – montera den virtuella hård disken för Nano Server och zippa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-189">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="c64fe-190">Överför zip-filen via en PowerShell-session online och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-190">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="c64fe-191">I båda fallen behöver du paketet Windows 10 x64 ZIP release.</span><span class="sxs-lookup"><span data-stu-id="c64fe-191">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="c64fe-192">Kör kommandona i en "administratör"-instans av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64fe-192">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="c64fe-193">Offline-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64fe-193">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="c64fe-194">Använd ditt favorit-zip-verktyg för att packa upp paketet till en katalog i den monterade Nano Server-avbildningen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-194">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="c64fe-195">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="c64fe-195">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="c64fe-196">Anslut till den inbyggda instansen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64fe-196">Connect to the built-in instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="c64fe-197">Följ instruktionerna för att skapa en fjärran sluten slut punkt med hjälp av ["en annan instans teknik"][].</span><span class="sxs-lookup"><span data-stu-id="c64fe-197">Follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="c64fe-198">Online-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64fe-198">Online Deployment of PowerShell</span></span>

<span data-ttu-id="c64fe-199">Distribuera PowerShell till Nano Server med hjälp av följande steg.</span><span class="sxs-lookup"><span data-stu-id="c64fe-199">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="c64fe-200">Ansluta till den inbyggda instansen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64fe-200">Connect to the built-in instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="c64fe-201">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="c64fe-201">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="c64fe-202">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="c64fe-202">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="c64fe-203">Extrahera ZIP-filen</span><span class="sxs-lookup"><span data-stu-id="c64fe-203">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="c64fe-204">Om du vill använda WSMan-baserad fjärr kommunikation följer du anvisningarna för att skapa en slut punkt för fjärr kommunikation med hjälp av ["en annan instans teknik"][].</span><span class="sxs-lookup"><span data-stu-id="c64fe-204">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="c64fe-205">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="c64fe-205">Install as a .NET Global tool</span></span>

<span data-ttu-id="c64fe-206">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="c64fe-206">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="c64fe-207">Installations programmet för dotNET-verktyget lägger till `$env:USERPROFILE\dotnet\tools` i din `$env:PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="c64fe-207">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="c64fe-208">Men det gränssnitt som körs har inte uppdaterats `$env:PATH` .</span><span class="sxs-lookup"><span data-stu-id="c64fe-208">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="c64fe-209">Du kan starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="c64fe-209">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="install-powershell-via-winget"></a><span data-ttu-id="c64fe-210">Installera PowerShell via Winget</span><span class="sxs-lookup"><span data-stu-id="c64fe-210">Install PowerShell via Winget</span></span>

<span data-ttu-id="c64fe-211">Med `winget` kommando rads verktyget kan utvecklare identifiera, installera, uppgradera, ta bort och konfigurera program på Windows 10-datorer.</span><span class="sxs-lookup"><span data-stu-id="c64fe-211">The `winget` command-line tool enables developers to discover, install, upgrade, remove, and configure applications on Windows 10 computers.</span></span> <span data-ttu-id="c64fe-212">Det här verktyget är klient gränssnittet för Windows Package Manager-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c64fe-212">This tool is the client interface to the Windows Package Manager service.</span></span>

> [!NOTE]
> <span data-ttu-id="c64fe-213">`winget`Verktyget är för närvarande en för hands version.</span><span class="sxs-lookup"><span data-stu-id="c64fe-213">The `winget` tool is currently a preview.</span></span> <span data-ttu-id="c64fe-214">Alla planerade funktioner är inte tillgängliga för tillfället.</span><span class="sxs-lookup"><span data-stu-id="c64fe-214">Not all planned functionality is available at this time.</span></span>
> <span data-ttu-id="c64fe-215">Du bör inte använda den här metoden i ett scenario för produktions distribution.</span><span class="sxs-lookup"><span data-stu-id="c64fe-215">You should not use this method in a production deployment scenario.</span></span> <span data-ttu-id="c64fe-216">I [Winget] -dokumentationen finns en lista över system krav och installations anvisningar.</span><span class="sxs-lookup"><span data-stu-id="c64fe-216">See the [winget] documentation for a list of system requirements and install instructions.</span></span>

<span data-ttu-id="c64fe-217">Följande kommandon kan användas för att installera PowerShell med de publicerade `winget` paketen:</span><span class="sxs-lookup"><span data-stu-id="c64fe-217">The following commands can be used to install PowerShell using the published `winget` packages:</span></span>

1. <span data-ttu-id="c64fe-218">Sök efter den senaste versionen av PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64fe-218">Search for the latest version of PowerShell</span></span>

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.1.1
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.1-preview.5
   ```

1. <span data-ttu-id="c64fe-219">Installera en version av PowerShell med `--exact` parametern</span><span class="sxs-lookup"><span data-stu-id="c64fe-219">Install a version of PowerShell using the `--exact` parameter</span></span>

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="installing-from-the-microsoft-store"></a><span data-ttu-id="c64fe-220"><a id="msix" />Installera från Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="c64fe-220"><a id="msix" />Installing from the Microsoft Store</span></span>

<span data-ttu-id="c64fe-221">PowerShell 7,1 har publicerats till Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="c64fe-221">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="c64fe-222">Du hittar PowerShell-versionen på [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) webbplats eller i Store-programmet i Windows.</span><span class="sxs-lookup"><span data-stu-id="c64fe-222">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="c64fe-223">Fördelar med Microsoft Store-paketet:</span><span class="sxs-lookup"><span data-stu-id="c64fe-223">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="c64fe-224">Automatiska uppdateringar har skapats direkt i Windows 10</span><span class="sxs-lookup"><span data-stu-id="c64fe-224">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="c64fe-225">Integreras med andra mekanismer för program varu distribution som Intune och SCCM</span><span class="sxs-lookup"><span data-stu-id="c64fe-225">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

<span data-ttu-id="c64fe-226">Begränsningar:</span><span class="sxs-lookup"><span data-stu-id="c64fe-226">Limitations:</span></span>

<span data-ttu-id="c64fe-227">MSIX-paket körs i ett program begränsat läge som virtualiserar åtkomst till vissa fil system och register platser.</span><span class="sxs-lookup"><span data-stu-id="c64fe-227">MSIX packages run in an application sandbox that virtualizes access to some filesystem and registry locations.</span></span>

- <span data-ttu-id="c64fe-228">Alla register ändringar under HKEY_CURRENT_USER kopieras vid skrivning till en privat plats per användare per app.</span><span class="sxs-lookup"><span data-stu-id="c64fe-228">All registry changes under HKEY_CURRENT_USER are copied on write to a private, per-user, per-app location.</span></span> <span data-ttu-id="c64fe-229">Dessa värden är därför inte tillgängliga för andra program.</span><span class="sxs-lookup"><span data-stu-id="c64fe-229">Therefore, those values are not available to other applications.</span></span>
- <span data-ttu-id="c64fe-230">Eventuella konfigurations inställningar på system nivå som lagras i `$PSHOME` kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="c64fe-230">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="c64fe-231">Detta inkluderar WSMAN-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-231">This includes the WSMAN configuration.</span></span> <span data-ttu-id="c64fe-232">Detta förhindrar att fjärrsessioner ansluter till Store-baserade installationer av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64fe-232">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="c64fe-233">Konfigurationer på användar nivå och SSH-fjärrkommunikation stöds.</span><span class="sxs-lookup"><span data-stu-id="c64fe-233">User-level configurations and SSH remoting are supported.</span></span>

<span data-ttu-id="c64fe-234">Mer information finns i [förstå hur paketerade skrivbordsappar körs i Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes).</span><span class="sxs-lookup"><span data-stu-id="c64fe-234">For more information, see [Understanding how packaged desktop apps run on Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes).</span></span>

### <a name="using-the-msix-package"></a><span data-ttu-id="c64fe-235">Använda MSIX-paketet</span><span class="sxs-lookup"><span data-stu-id="c64fe-235">Using the MSIX package</span></span>

> [!NOTE]
> <span data-ttu-id="c64fe-236">I för hands versioner av PowerShell ingår ett MSIX-paket.</span><span class="sxs-lookup"><span data-stu-id="c64fe-236">The preview builds of PowerShell include an MSIX package.</span></span> <span data-ttu-id="c64fe-237">MSIX-paketet stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="c64fe-237">The MSIX package is not officially supported.</span></span> <span data-ttu-id="c64fe-238">Paketet är konstruerat för test ändamål under för hands versions perioden.</span><span class="sxs-lookup"><span data-stu-id="c64fe-238">The package is built for testing purposes during the preview period.</span></span>

<span data-ttu-id="c64fe-239">Om du vill installera MSIX-paketet manuellt på en Windows 10-klient laddar du ned MSIX-paketet från vår GitHub [Release] [releases]-sida.</span><span class="sxs-lookup"><span data-stu-id="c64fe-239">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="c64fe-240">Rulla ned till **till gångar** -avsnittet i den version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="c64fe-240">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="c64fe-241">Avsnittet till gångar kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="c64fe-241">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="c64fe-242">MSIX-filen ser ut så här – `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="c64fe-242">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="c64fe-243">Du måste använda cmdleten för att installera paketet `Add-AppxPackage` .</span><span class="sxs-lookup"><span data-stu-id="c64fe-243">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="c64fe-244">Så här skapar du en fjärran sluten slut punkt</span><span class="sxs-lookup"><span data-stu-id="c64fe-244">How to create a remoting endpoint</span></span>

<span data-ttu-id="c64fe-245">PowerShell stöder PowerShell Remoting-protokollet (PSRP) via både WSMan och SSH.</span><span class="sxs-lookup"><span data-stu-id="c64fe-245">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="c64fe-246">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="c64fe-246">For more information, see:</span></span>

- <span data-ttu-id="c64fe-247">[SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="c64fe-247">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="c64fe-248">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="c64fe-248">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="upgrading-an-existing-installation"></a><span data-ttu-id="c64fe-249">Uppgradera en befintlig installation</span><span class="sxs-lookup"><span data-stu-id="c64fe-249">Upgrading an existing installation</span></span>

<span data-ttu-id="c64fe-250">För bästa resultat vid uppgraderingen bör du använda samma installations metod som du använde när du först installerade PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64fe-250">For best results when upgrading, you should use the same install method you used when you first installed PowerShell.</span></span> <span data-ttu-id="c64fe-251">Varje installations metod installerar PowerShell på en annan plats.</span><span class="sxs-lookup"><span data-stu-id="c64fe-251">Each installation method installs PowerShell in a different location.</span></span> <span data-ttu-id="c64fe-252">Om du inte är säker på hur PowerShell installerades kan du jämföra den installerade platsen med paket informationen i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="c64fe-252">If you are not sure how PowerShell was installed, you can compare the installed location with the package information in this article.</span></span> <span data-ttu-id="c64fe-253">Om du har installerat via MSI-paketet visas den informationen i **program och funktioner** på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="c64fe-253">If you installed via the MSI package, that information appears in the **Programs and Features** Control Panel.</span></span>

## <a name="installation-support"></a><span data-ttu-id="c64fe-254">Installations stöd</span><span class="sxs-lookup"><span data-stu-id="c64fe-254">Installation support</span></span>

<span data-ttu-id="c64fe-255">Microsoft stöder installations metoderna i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="c64fe-255">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="c64fe-256">Det kan finnas andra installations metoder som är tillgängliga från andra källor.</span><span class="sxs-lookup"><span data-stu-id="c64fe-256">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="c64fe-257">Dessa verktyg och metoder kan fungera, men Microsoft stöder inte dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="c64fe-257">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->

[förhandsgranskningsvyn]: https://aka.ms/powershell-release?tag=preview
[preview]: https://aka.ms/powershell-release?tag=preview
[senaste]: https://aka.ms/powershell-release?tag=stable
[latest]: https://aka.ms/powershell-release?tag=stable
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
["en annan instans teknik"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
["another instance technique"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Importera – PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
