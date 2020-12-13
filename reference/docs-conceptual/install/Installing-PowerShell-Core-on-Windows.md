---
title: Installera PowerShell i Windows
description: Information om hur du installerar PowerShell på Windows
ms.date: 11/11/2020
ms.openlocfilehash: 039db904a315bd3ad3f4e1358d414c98c3a84be5
ms.sourcegitcommit: 7f712e12ec5b3f3f3e695da804b050ea0ce58b3a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94661434"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="c4a90-103">Installera PowerShell i Windows</span><span class="sxs-lookup"><span data-stu-id="c4a90-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="c4a90-104">Det finns flera sätt att installera PowerShell i Windows.</span><span class="sxs-lookup"><span data-stu-id="c4a90-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c4a90-105">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="c4a90-105">Prerequisites</span></span>

<span data-ttu-id="c4a90-106">Den senaste versionen av PowerShell stöds på Windows 7 SP1, Server 2008 R2 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="c4a90-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="c4a90-107">Om du vill aktivera PowerShell-fjärrkommunikation över WSMan måste följande krav vara uppfyllda:</span><span class="sxs-lookup"><span data-stu-id="c4a90-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="c4a90-108">Installera [Universal C runtime](https://www.microsoft.com/download/details.aspx?id=50410) på Windows-versioner predating Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c4a90-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="c4a90-109">Den är tillgänglig via direkt hämtning eller Windows Update.</span><span class="sxs-lookup"><span data-stu-id="c4a90-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="c4a90-110">Fullständigt installerade system har redan det här paketet installerat.</span><span class="sxs-lookup"><span data-stu-id="c4a90-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="c4a90-111">Installera Windows Management Framework (WMF) 4,0 eller senare på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="c4a90-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="c4a90-112">Mer information om WMF finns i [Översikt över WMF](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="c4a90-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="c4a90-113">Ladda ned installations paketet</span><span class="sxs-lookup"><span data-stu-id="c4a90-113">Download the installer package</span></span>

<span data-ttu-id="c4a90-114">Om du vill installera PowerShell på Windows laddar du ned det [senaste][] installations paketet från GitHub.</span><span class="sxs-lookup"><span data-stu-id="c4a90-114">To install PowerShell on Windows, download the [latest][] install package from GitHub.</span></span> <span data-ttu-id="c4a90-115">Du kan också hitta den senaste för hands versionen på sidan [versioner][] .</span><span class="sxs-lookup"><span data-stu-id="c4a90-115">You can also find the latest preview version on the [releases][] page.</span></span> <span data-ttu-id="c4a90-116">Rulla ned till **till gångar** -avsnittet på sidan version.</span><span class="sxs-lookup"><span data-stu-id="c4a90-116">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="c4a90-117">Avsnittet **till gångar** kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="c4a90-117">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="c4a90-118"><a id="msi" />Installera MSI-paketet</span><span class="sxs-lookup"><span data-stu-id="c4a90-118"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="c4a90-119">MSI-filen ser ut så här `PowerShell-<version>-win-<os-arch>.msi` .</span><span class="sxs-lookup"><span data-stu-id="c4a90-119">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="c4a90-120">Exempel:</span><span class="sxs-lookup"><span data-stu-id="c4a90-120">For example:</span></span>

- `PowerShell-7.1.0-win-x64.msi`
- `PowerShell-7.1.0-win-x86.msi`

<span data-ttu-id="c4a90-121">När du har laddat ned dubbelklickar du på installations programmet och följer anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="c4a90-121">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="c4a90-122">Installations programmet skapar en genväg på Start-menyn i Windows.</span><span class="sxs-lookup"><span data-stu-id="c4a90-122">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="c4a90-123">Som standard installeras paketet på `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="c4a90-123">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="c4a90-124">Du kan starta PowerShell via Start-menyn eller `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="c4a90-124">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="c4a90-125">PowerShell 7,1 installeras i en ny katalog och körs sida vid sida med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="c4a90-125">PowerShell 7.1 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span>
> <span data-ttu-id="c4a90-126">PowerShell 7,1 är en uppgradering på plats som ersätter PowerShell 6. x.</span><span class="sxs-lookup"><span data-stu-id="c4a90-126">PowerShell 7.1 is an in-place upgrade that replaces PowerShell 6.x.</span></span> <span data-ttu-id="c4a90-127">eller PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="c4a90-127">or PowerShell 7.0.</span></span>
>
> - <span data-ttu-id="c4a90-128">PowerShell 7,1 är installerat på `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="c4a90-128">PowerShell 7.1 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="c4a90-129">`$env:ProgramFiles\PowerShell\7`Mappen läggs till`$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="c4a90-129">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="c4a90-130">`$env:ProgramFiles\PowerShell\6`Mappen tas bort</span><span class="sxs-lookup"><span data-stu-id="c4a90-130">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="c4a90-131">Om du behöver köra PowerShell 7,1 sida vid sida med andra versioner använder du [zip-installations](#zip) metoden för att installera den andra versionen i en annan mapp.</span><span class="sxs-lookup"><span data-stu-id="c4a90-131">If you need to run PowerShell 7.1 side-by-side with other versions, use the [ZIP install](#zip) method to install the other version to a different folder.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="c4a90-132">Administrativ installation från kommando raden</span><span class="sxs-lookup"><span data-stu-id="c4a90-132">Administrative install from the command line</span></span>

<span data-ttu-id="c4a90-133">MSI-paket kan installeras från kommando raden och gör det möjligt för administratörer att distribuera paket utan användar interaktion.</span><span class="sxs-lookup"><span data-stu-id="c4a90-133">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="c4a90-134">MSI-paketet innehåller följande egenskaper för att kontrol lera installations alternativen:</span><span class="sxs-lookup"><span data-stu-id="c4a90-134">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="c4a90-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – den här egenskapen styr alternativet för att lägga till det **Öppna PowerShell** -objektet i snabb menyn i Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="c4a90-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="c4a90-136">**ENABLE_PSREMOTING** – den här egenskapen styr alternativet för att aktivera PowerShell-fjärrkommunikation under installationen.</span><span class="sxs-lookup"><span data-stu-id="c4a90-136">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="c4a90-137">**REGISTER_MANIFEST** – den här egenskapen styr alternativet för registrering av Windows händelse loggnings manifestet.</span><span class="sxs-lookup"><span data-stu-id="c4a90-137">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="c4a90-138">I följande exempel visas hur du tyst installerar PowerShell med alla installations alternativ aktiverade.</span><span class="sxs-lookup"><span data-stu-id="c4a90-138">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.1.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="c4a90-139">En fullständig lista över kommando rads alternativ för `Msiexec.exe` finns i [kommando rads alternativ](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="c4a90-139">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

### <a name="registry-keys-created-during-installation"></a><span data-ttu-id="c4a90-140">Register nycklar som skapas under installationen</span><span class="sxs-lookup"><span data-stu-id="c4a90-140">Registry keys created during installation</span></span>

<span data-ttu-id="c4a90-141">Från och med PowerShell 7,1 skapar MSI-paketet register nycklar som lagrar installations platsen och versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4a90-141">Beginning in PowerShell 7.1, the MSI package creates registry keys that store the installation location and version of PowerShell.</span></span> <span data-ttu-id="c4a90-142">Dessa värden finns i `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` .</span><span class="sxs-lookup"><span data-stu-id="c4a90-142">These values are located in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`.</span></span> <span data-ttu-id="c4a90-143">Värdet för `<GUID>` är unikt för varje build-typ (version eller förhands granskning), huvud version och arkitektur.</span><span class="sxs-lookup"><span data-stu-id="c4a90-143">The value of `<GUID>` is unique for each build type (release or preview), major version, and architecture.</span></span>

|    <span data-ttu-id="c4a90-144">Frisläpp</span><span class="sxs-lookup"><span data-stu-id="c4a90-144">Release</span></span>    | <span data-ttu-id="c4a90-145">Arkitektur</span><span class="sxs-lookup"><span data-stu-id="c4a90-145">Architecture</span></span> |                                          <span data-ttu-id="c4a90-146">Registernyckel</span><span class="sxs-lookup"><span data-stu-id="c4a90-146">Registry Key</span></span>                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c4a90-147">7.1. x-version</span><span class="sxs-lookup"><span data-stu-id="c4a90-147">7.1.x Release</span></span> |     <span data-ttu-id="c4a90-148">x86</span><span class="sxs-lookup"><span data-stu-id="c4a90-148">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| <span data-ttu-id="c4a90-149">7.1. x-version</span><span class="sxs-lookup"><span data-stu-id="c4a90-149">7.1.x Release</span></span> |     <span data-ttu-id="c4a90-150">x64</span><span class="sxs-lookup"><span data-stu-id="c4a90-150">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| <span data-ttu-id="c4a90-151">7.1. x-förhandsgranskning</span><span class="sxs-lookup"><span data-stu-id="c4a90-151">7.1.x Preview</span></span> |     <span data-ttu-id="c4a90-152">x86</span><span class="sxs-lookup"><span data-stu-id="c4a90-152">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| <span data-ttu-id="c4a90-153">7.1. x-förhandsgranskning</span><span class="sxs-lookup"><span data-stu-id="c4a90-153">7.1.x Preview</span></span> |     <span data-ttu-id="c4a90-154">x64</span><span class="sxs-lookup"><span data-stu-id="c4a90-154">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

<span data-ttu-id="c4a90-155">Detta kan användas av administratörer och utvecklare för att hitta sökvägen till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4a90-155">This can be used by administrators and developers to find the path to PowerShell.</span></span> <span data-ttu-id="c4a90-156">`<GUID>`Värdena är desamma för alla för hands versioner och del versioner.</span><span class="sxs-lookup"><span data-stu-id="c4a90-156">The `<GUID>` values will be the same for all preview and minor version releases.</span></span> <span data-ttu-id="c4a90-157">`<GUID>`Värdena ändras för varje större version.</span><span class="sxs-lookup"><span data-stu-id="c4a90-157">The `<GUID>` values are changed for each major release.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="c4a90-158"><a id="zip" />Installera ZIP-paketet</span><span class="sxs-lookup"><span data-stu-id="c4a90-158"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="c4a90-159">Det finns PowerShell-Arkiv för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="c4a90-159">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="c4a90-160">Hämta något av följande ZIP-arkiv från sidan [release][releases] .</span><span class="sxs-lookup"><span data-stu-id="c4a90-160">Download one of the following ZIP archives from the [releases][releases] page.</span></span>

- <span data-ttu-id="c4a90-161">PowerShell-7.1.0-win-x64.zip</span><span class="sxs-lookup"><span data-stu-id="c4a90-161">PowerShell-7.1.0-win-x64.zip</span></span>
- <span data-ttu-id="c4a90-162">PowerShell-7.1.0-win-x86.zip</span><span class="sxs-lookup"><span data-stu-id="c4a90-162">PowerShell-7.1.0-win-x86.zip</span></span>
- <span data-ttu-id="c4a90-163">PowerShell-7.1.0-win-arm64.zip</span><span class="sxs-lookup"><span data-stu-id="c4a90-163">PowerShell-7.1.0-win-arm64.zip</span></span>
- <span data-ttu-id="c4a90-164">PowerShell-7.1.0-win-arm32.zip</span><span class="sxs-lookup"><span data-stu-id="c4a90-164">PowerShell-7.1.0-win-arm32.zip</span></span>

<span data-ttu-id="c4a90-165">Beroende på hur du laddar ned filen kan du behöva avblockera filen med hjälp av `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c4a90-165">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="c4a90-166">Zippa upp innehållet till valfri plats och kör `pwsh.exe` därifrån.</span><span class="sxs-lookup"><span data-stu-id="c4a90-166">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="c4a90-167">Till skillnad från när du installerar MSI-paketen söker inte du efter krav i ZIP-arkivet.</span><span class="sxs-lookup"><span data-stu-id="c4a90-167">Unlike installing the MSI packages, installing the ZIP archive doesn't check for prerequisites.</span></span> <span data-ttu-id="c4a90-168">Se till att du uppfyller [kraven](#prerequisites)för fjärr kommunikation över WSMan för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="c4a90-168">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

<span data-ttu-id="c4a90-169">Använd den här metoden för att installera den ARM-baserade versionen av PowerShell på datorer som Microsoft Surface Pro X. För bästa resultat bör du installera PowerShell i till- `$env:ProgramFiles\PowerShell\7` mappen.</span><span class="sxs-lookup"><span data-stu-id="c4a90-169">Use this method to install the ARM-based version of PowerShell on computers like the Microsoft Surface Pro X. For best results, install PowerShell to the to `$env:ProgramFiles\PowerShell\7` folder.</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="c4a90-170">Distribuera i Windows 10 IoT Enterprise</span><span class="sxs-lookup"><span data-stu-id="c4a90-170">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="c4a90-171">Windows 10 IoT Enterprise levereras med Windows PowerShell, som vi kan använda för att distribuera PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c4a90-171">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="c4a90-172">Skapa `PSSession` till mål enhet</span><span class="sxs-lookup"><span data-stu-id="c4a90-172">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. <span data-ttu-id="c4a90-173">Kopiera ZIP-paketet till enheten</span><span class="sxs-lookup"><span data-stu-id="c4a90-173">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. <span data-ttu-id="c4a90-174">Anslut till enheten och Expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="c4a90-174">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. <span data-ttu-id="c4a90-175">Konfigurera fjärr kommunikation till PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="c4a90-175">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. <span data-ttu-id="c4a90-176">Anslut till PowerShell 7-slutpunkt på enhet</span><span class="sxs-lookup"><span data-stu-id="c4a90-176">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="c4a90-177">Distribuera på Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="c4a90-177">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="c4a90-178">Windows 10 IoT Core lägger till Windows PowerShell när du inkluderar _IOT_POWERSHELL_ funktion som vi kan använda för att distribuera PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="c4a90-178">Windows 10 IoT Core adds Windows PowerShell when you include _IOT_POWERSHELL_ feature, which we can use to deploy PowerShell 7.</span></span> <span data-ttu-id="c4a90-179">Stegen som definieras ovan för Windows 10 IoT Enterprise kan också följas av IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c4a90-179">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="c4a90-180">För att lägga till den senaste PowerShell-versionen i leverans avbildningen använder du kommandot [import-PSCoreRelease][] för att inkludera paketet i workarea och lägga till _OPENSRC_POWERSHELL_ funktion i avbildningen.</span><span class="sxs-lookup"><span data-stu-id="c4a90-180">For adding the latest PowerShell in the shipping image, use [Import-PSCoreRelease][] command to include the package in the workarea and add _OPENSRC_POWERSHELL_ feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="c4a90-181">Windows PowerShell läggs inte till i ARM64-arkitekturen när du tar med _IOT_POWERSHELL_.</span><span class="sxs-lookup"><span data-stu-id="c4a90-181">For ARM64 architecture, Windows PowerShell is not added when you include _IOT_POWERSHELL_.</span></span> <span data-ttu-id="c4a90-182">Det innebär att zip-baserad installation inte fungerar.</span><span class="sxs-lookup"><span data-stu-id="c4a90-182">So the zip based install will not work.</span></span> <span data-ttu-id="c4a90-183">Du måste använda `Import-PSCoreRelease` kommandot för att lägga till det i avbildningen.</span><span class="sxs-lookup"><span data-stu-id="c4a90-183">You will need to use `Import-PSCoreRelease` command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="c4a90-184">Distribuera på Nano Server</span><span class="sxs-lookup"><span data-stu-id="c4a90-184">Deploying on Nano Server</span></span>

<span data-ttu-id="c4a90-185">Dessa instruktioner förutsätter att Nano-servern är ett "" "" "-"-OS som har en version av PowerShell som redan körs på den.</span><span class="sxs-lookup"><span data-stu-id="c4a90-185">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="c4a90-186">Mer information finns i dokumentationen för [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) .</span><span class="sxs-lookup"><span data-stu-id="c4a90-186">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="c4a90-187">PowerShell-binärfiler kan distribueras med två olika metoder.</span><span class="sxs-lookup"><span data-stu-id="c4a90-187">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="c4a90-188">Offline – montera den virtuella hård disken för Nano Server och zippa upp innehållet i zip-filen till den valda platsen i den monterade avbildningen.</span><span class="sxs-lookup"><span data-stu-id="c4a90-188">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="c4a90-189">Överför zip-filen via en PowerShell-session online och packa upp den på den valda platsen.</span><span class="sxs-lookup"><span data-stu-id="c4a90-189">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="c4a90-190">I båda fallen behöver du paketet Windows 10 x64 ZIP release.</span><span class="sxs-lookup"><span data-stu-id="c4a90-190">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="c4a90-191">Kör kommandona i en "administratör"-instans av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4a90-191">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="c4a90-192">Offline-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4a90-192">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="c4a90-193">Använd ditt favorit-zip-verktyg för att packa upp paketet till en katalog i den monterade Nano Server-avbildningen.</span><span class="sxs-lookup"><span data-stu-id="c4a90-193">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="c4a90-194">Demontera avbildningen och starta den.</span><span class="sxs-lookup"><span data-stu-id="c4a90-194">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="c4a90-195">Anslut till den inbyggda instansen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4a90-195">Connect to the built-in instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="c4a90-196">Följ instruktionerna för att skapa en fjärran sluten slut punkt med hjälp av ["en annan instans teknik"][].</span><span class="sxs-lookup"><span data-stu-id="c4a90-196">Follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="c4a90-197">Online-distribution av PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4a90-197">Online Deployment of PowerShell</span></span>

<span data-ttu-id="c4a90-198">Distribuera PowerShell till Nano Server med hjälp av följande steg.</span><span class="sxs-lookup"><span data-stu-id="c4a90-198">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="c4a90-199">Ansluta till den inbyggda instansen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4a90-199">Connect to the built-in instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="c4a90-200">Kopiera filen till Nano Server-instansen</span><span class="sxs-lookup"><span data-stu-id="c4a90-200">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="c4a90-201">Ange sessionen</span><span class="sxs-lookup"><span data-stu-id="c4a90-201">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="c4a90-202">Extrahera ZIP-filen</span><span class="sxs-lookup"><span data-stu-id="c4a90-202">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="c4a90-203">Om du vill använda WSMan-baserad fjärr kommunikation följer du anvisningarna för att skapa en slut punkt för fjärr kommunikation med hjälp av ["en annan instans teknik"][].</span><span class="sxs-lookup"><span data-stu-id="c4a90-203">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="c4a90-204">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="c4a90-204">Install as a .NET Global tool</span></span>

<span data-ttu-id="c4a90-205">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="c4a90-205">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="c4a90-206">Installations programmet för dotNET-verktyget lägger till `$env:USERPROFILE\dotnet\tools` i din `$env:PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="c4a90-206">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="c4a90-207">Men det gränssnitt som körs har inte uppdaterats `$env:PATH` .</span><span class="sxs-lookup"><span data-stu-id="c4a90-207">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="c4a90-208">Du kan starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="c4a90-208">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="install-powershell-via-winget"></a><span data-ttu-id="c4a90-209">Installera PowerShell via Winget</span><span class="sxs-lookup"><span data-stu-id="c4a90-209">Install PowerShell via Winget</span></span>

<span data-ttu-id="c4a90-210">Med `winget` kommando rads verktyget kan utvecklare identifiera, installera, uppgradera, ta bort och konfigurera program på Windows 10-datorer.</span><span class="sxs-lookup"><span data-stu-id="c4a90-210">The `winget` command-line tool enables developers to discover, install, upgrade, remove, and configure applications on Windows 10 computers.</span></span> <span data-ttu-id="c4a90-211">Det här verktyget är klient gränssnittet för Windows Package Manager-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c4a90-211">This tool is the client interface to the Windows Package Manager service.</span></span>

> [!NOTE]
> <span data-ttu-id="c4a90-212">`winget`Verktyget är för närvarande en för hands version.</span><span class="sxs-lookup"><span data-stu-id="c4a90-212">The `winget` tool is currently a preview.</span></span> <span data-ttu-id="c4a90-213">Alla planerade funktioner är inte tillgängliga för tillfället.</span><span class="sxs-lookup"><span data-stu-id="c4a90-213">Not all planned functionality is available at this time.</span></span>
> <span data-ttu-id="c4a90-214">Du bör inte använda den här metoden i ett scenario för produktions distribution.</span><span class="sxs-lookup"><span data-stu-id="c4a90-214">You should not use this method in a production deployment scenario.</span></span> <span data-ttu-id="c4a90-215">I [Winget] -dokumentationen finns en lista över system krav och installations anvisningar.</span><span class="sxs-lookup"><span data-stu-id="c4a90-215">See the [winget] documentation for a list of system requirements and install instructions.</span></span>

<span data-ttu-id="c4a90-216">Följande kommandon kan användas för att installera PowerShell med de publicerade `winget` paketen:</span><span class="sxs-lookup"><span data-stu-id="c4a90-216">The following commands can be used to install PowerShell using the published `winget` packages:</span></span>

1. <span data-ttu-id="c4a90-217">Sök efter den senaste versionen av PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4a90-217">Search for the latest version of PowerShell</span></span>

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.1.0
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.0-preview.5
   ```

1. <span data-ttu-id="c4a90-218">Installera en version av PowerShell med `--exact` parametern</span><span class="sxs-lookup"><span data-stu-id="c4a90-218">Install a version of PowerShell using the `--exact` parameter</span></span>

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="installing-from-the-microsoft-store"></a><span data-ttu-id="c4a90-219"><a id="msix" />Installera från Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="c4a90-219"><a id="msix" />Installing from the Microsoft Store</span></span>

<span data-ttu-id="c4a90-220">PowerShell 7,1 har publicerats till Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="c4a90-220">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="c4a90-221">Du hittar PowerShell-versionen på [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) webbplats eller i Store-programmet i Windows.</span><span class="sxs-lookup"><span data-stu-id="c4a90-221">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="c4a90-222">Fördelar med Microsoft Store-paketet:</span><span class="sxs-lookup"><span data-stu-id="c4a90-222">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="c4a90-223">Automatiska uppdateringar har skapats direkt i Windows 10</span><span class="sxs-lookup"><span data-stu-id="c4a90-223">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="c4a90-224">Integreras med andra mekanismer för program varu distribution som Intune och SCCM</span><span class="sxs-lookup"><span data-stu-id="c4a90-224">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

<span data-ttu-id="c4a90-225">Begränsningar:</span><span class="sxs-lookup"><span data-stu-id="c4a90-225">Limitations:</span></span>

<span data-ttu-id="c4a90-226">MSIX-paket körs i ett program begränsat läge som virtualiserar åtkomst till vissa fil system och register platser.</span><span class="sxs-lookup"><span data-stu-id="c4a90-226">MSIX packages run in an application sandbox that virtualizes access to some filesystem and registry locations.</span></span>

- <span data-ttu-id="c4a90-227">Alla register ändringar under HKEY_CURRENT_USER kopieras vid skrivning till en privat plats per användare per app.</span><span class="sxs-lookup"><span data-stu-id="c4a90-227">All registry changes under HKEY_CURRENT_USER are copied on write to a private, per-user, per-app location.</span></span> <span data-ttu-id="c4a90-228">Dessa värden är därför inte tillgängliga för andra program.</span><span class="sxs-lookup"><span data-stu-id="c4a90-228">Therefore, those values are not available to other applications.</span></span>
- <span data-ttu-id="c4a90-229">Eventuella konfigurations inställningar på system nivå som lagras i `$PSHOME` kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="c4a90-229">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="c4a90-230">Detta inkluderar WSMAN-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="c4a90-230">This includes the WSMAN configuration.</span></span> <span data-ttu-id="c4a90-231">Detta förhindrar att fjärrsessioner ansluter till Store-baserade installationer av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4a90-231">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="c4a90-232">Konfigurationer på användar nivå och SSH-fjärrkommunikation stöds.</span><span class="sxs-lookup"><span data-stu-id="c4a90-232">User-level configurations and SSH remoting are supported.</span></span>

<span data-ttu-id="c4a90-233">Mer information finns i [förstå hur paketerade skrivbordsappar körs i Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes).</span><span class="sxs-lookup"><span data-stu-id="c4a90-233">For more information, see [Understanding how packaged desktop apps run on Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes).</span></span>

### <a name="using-the-msix-package"></a><span data-ttu-id="c4a90-234">Använda MSIX-paketet</span><span class="sxs-lookup"><span data-stu-id="c4a90-234">Using the MSIX package</span></span>

> [!NOTE]
> <span data-ttu-id="c4a90-235">I för hands versioner av PowerShell ingår ett MSIX-paket.</span><span class="sxs-lookup"><span data-stu-id="c4a90-235">The preview builds of PowerShell include an MSIX package.</span></span> <span data-ttu-id="c4a90-236">MSIX-paketet stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="c4a90-236">The MSIX package is not officially supported.</span></span> <span data-ttu-id="c4a90-237">Paketet är konstruerat för test ändamål under för hands versions perioden.</span><span class="sxs-lookup"><span data-stu-id="c4a90-237">The package is built for testing purposes during the preview period.</span></span>

<span data-ttu-id="c4a90-238">Om du vill installera MSIX-paketet manuellt på en Windows 10-klient laddar du ned MSIX-paketet från vår versions[sida för] GitHub- [versioner].</span><span class="sxs-lookup"><span data-stu-id="c4a90-238">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="c4a90-239">Rulla ned till **till gångar** -avsnittet i den version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="c4a90-239">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="c4a90-240">Avsnittet till gångar kan vara minimerat, så du kan behöva klicka för att expandera det.</span><span class="sxs-lookup"><span data-stu-id="c4a90-240">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="c4a90-241">MSIX-filen ser ut så här – `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="c4a90-241">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="c4a90-242">Du måste använda cmdleten för att installera paketet `Add-AppxPackage` .</span><span class="sxs-lookup"><span data-stu-id="c4a90-242">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="c4a90-243">Så här skapar du en fjärran sluten slut punkt</span><span class="sxs-lookup"><span data-stu-id="c4a90-243">How to create a remoting endpoint</span></span>

<span data-ttu-id="c4a90-244">PowerShell stöder PowerShell Remoting-protokollet (PSRP) via både WSMan och SSH.</span><span class="sxs-lookup"><span data-stu-id="c4a90-244">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="c4a90-245">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="c4a90-245">For more information, see:</span></span>

- <span data-ttu-id="c4a90-246">[SSH-fjärrkommunikation i PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="c4a90-246">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="c4a90-247">[WSMan-fjärrkommunikation i PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="c4a90-247">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="upgrading-an-existing-installation"></a><span data-ttu-id="c4a90-248">Uppgradera en befintlig installation</span><span class="sxs-lookup"><span data-stu-id="c4a90-248">Upgrading an existing installation</span></span>

<span data-ttu-id="c4a90-249">För bästa resultat vid uppgraderingen bör du använda samma installations metod som du använde när du först installerade PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4a90-249">For best results when upgrading, you should use the same install method you used when you first installed PowerShell.</span></span> <span data-ttu-id="c4a90-250">Varje installations metod installerar PowerShell på en annan plats.</span><span class="sxs-lookup"><span data-stu-id="c4a90-250">Each installation method installs PowerShell in a different location.</span></span> <span data-ttu-id="c4a90-251">Om du inte är säker på hur PowerShell installerades kan du jämföra den installerade platsen med paket informationen i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="c4a90-251">If you are not sure how PowerShell was installed, you can compare the installed location with the package information in this article.</span></span> <span data-ttu-id="c4a90-252">Om du har installerat via MSI-paketet visas den informationen i **program och funktioner** på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="c4a90-252">If you installed via the MSI package, that information appears in the **Programs and Features** Control Panel.</span></span>

## <a name="installation-support"></a><span data-ttu-id="c4a90-253">Installations stöd</span><span class="sxs-lookup"><span data-stu-id="c4a90-253">Installation support</span></span>

<span data-ttu-id="c4a90-254">Microsoft stöder installations metoderna i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="c4a90-254">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="c4a90-255">Det kan finnas andra installations metoder som är tillgängliga från andra källor.</span><span class="sxs-lookup"><span data-stu-id="c4a90-255">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="c4a90-256">Dessa verktyg och metoder kan fungera, men Microsoft stöder inte dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="c4a90-256">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->

[exekutiv]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[senaste]: https://github.com/PowerShell/PowerShell/releases/latest
[latest]: https://github.com/PowerShell/PowerShell/releases/latest
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
["en annan instans teknik"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
["another instance technique"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Importera – PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
