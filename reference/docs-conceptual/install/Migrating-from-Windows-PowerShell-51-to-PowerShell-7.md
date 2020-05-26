---
title: Migrera från Windows PowerShell 5.1 till PowerShell 7
description: Uppdatera från PowerShell 5,1 till PowerShell 7 för dina Windows-plattformar.
ms.date: 03/25/2020
ms.openlocfilehash: cb14a4f159b6dc33f31386da4264c0ebb640aef8
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810577"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a><span data-ttu-id="281ed-103">Migrera från Windows PowerShell 5.1 till PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="281ed-103">Migrating from Windows PowerShell 5.1 to PowerShell 7</span></span>

<span data-ttu-id="281ed-104">PowerShell 7 är utformat för molnbaserade, lokala miljöer och hybrid miljöer och är förpackat med förbättringar och [nya funktioner](../whats-new/What-s-New-in-PowerShell-70.md).</span><span class="sxs-lookup"><span data-stu-id="281ed-104">Designed for cloud, on-premises, and hybrid environments, PowerShell 7 is packed with enhancements and [new features](../whats-new/What-s-New-in-PowerShell-70.md).</span></span>

- <span data-ttu-id="281ed-105">Installerar och körs sida vid sida med Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="281ed-105">Installs and runs side-by-side with Windows PowerShell</span></span>
- <span data-ttu-id="281ed-106">Förbättrad kompatibilitet med befintliga Windows PowerShell-moduler</span><span class="sxs-lookup"><span data-stu-id="281ed-106">Improved compatibility with existing Windows PowerShell modules</span></span>
- <span data-ttu-id="281ed-107">Nya språk funktioner, t. ex. ternära operatörer och`ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="281ed-107">New language features, like ternary operators and `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="281ed-108">Förbättrade prestanda</span><span class="sxs-lookup"><span data-stu-id="281ed-108">Improved performance</span></span>
- <span data-ttu-id="281ed-109">SSH-baserad fjärr kommunikation</span><span class="sxs-lookup"><span data-stu-id="281ed-109">SSH-based remoting</span></span>
- <span data-ttu-id="281ed-110">Samverkan mellan plattformar</span><span class="sxs-lookup"><span data-stu-id="281ed-110">Cross-platform interoperability</span></span>
- <span data-ttu-id="281ed-111">Stöd för Docker-behållare</span><span class="sxs-lookup"><span data-stu-id="281ed-111">Support for Docker containers</span></span>

<span data-ttu-id="281ed-112">PowerShell 7 fungerar sida vid sida med Windows PowerShell och du kan enkelt testa och jämföra versioner innan du distribuerar.</span><span class="sxs-lookup"><span data-stu-id="281ed-112">PowerShell 7 works side-by-side with Windows PowerShell letting you easily test and compare between editions before deployment.</span></span> <span data-ttu-id="281ed-113">Migrering är enkel, snabb och säker.</span><span class="sxs-lookup"><span data-stu-id="281ed-113">Migration is simple, quick, and safe.</span></span>

<span data-ttu-id="281ed-114">PowerShell 7 stöds i följande Windows-operativ system:</span><span class="sxs-lookup"><span data-stu-id="281ed-114">PowerShell 7 is supported on the following Windows operating systems:</span></span>

- <span data-ttu-id="281ed-115">Windows 8,1 och 10</span><span class="sxs-lookup"><span data-stu-id="281ed-115">Windows 8.1 and 10</span></span>
- <span data-ttu-id="281ed-116">Windows Server 2012, 2012 R2, 2016 och 2019</span><span class="sxs-lookup"><span data-stu-id="281ed-116">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>

<span data-ttu-id="281ed-117">PowerShell 7 körs också på macOS och flera Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="281ed-117">PowerShell 7 also runs on macOS and several Linux distributions.</span></span> <span data-ttu-id="281ed-118">En lista över operativ system som stöds och information om support livs cykeln finns i [PowerShell-Supportens livs cykel](/powershell/scripting/powershell-support-lifecycle).</span><span class="sxs-lookup"><span data-stu-id="281ed-118">For a list of supported operating systems and information about the support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="installing-powershell-7"></a><span data-ttu-id="281ed-119">Installera PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="281ed-119">Installing PowerShell 7</span></span>

<span data-ttu-id="281ed-120">Det finns flera tillgängliga alternativ för att installera PowerShell 7 för flexibilitet och för att stödja behoven hos IT, DevOps-tekniker och utvecklare.</span><span class="sxs-lookup"><span data-stu-id="281ed-120">For flexibility and to support the needs of IT, DevOps engineers, and developers, there are several options available to install PowerShell 7.</span></span> <span data-ttu-id="281ed-121">I de flesta fall kan installations alternativen minskas till följande metoder:</span><span class="sxs-lookup"><span data-stu-id="281ed-121">In most cases, the installation options can be reduced to the following methods:</span></span>

- <span data-ttu-id="281ed-122">Distribuera PowerShell med [MSI-paketet](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span><span class="sxs-lookup"><span data-stu-id="281ed-122">Deploy PowerShell using the [MSI package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span></span>
- <span data-ttu-id="281ed-123">Distribuera PowerShell med [zip-paketet](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span><span class="sxs-lookup"><span data-stu-id="281ed-123">Deploy PowerShell using the [ZIP package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span></span>

> [!NOTE]
> <span data-ttu-id="281ed-124">MSI-paketet kan distribueras och uppdateras med hanterings produkter som [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span><span class="sxs-lookup"><span data-stu-id="281ed-124">The MSI package can be deployed and updated with management products such as [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span></span> <span data-ttu-id="281ed-125">Hämta paketen från [GitHub release-sidan](https://github.com/PowerShell/PowerShell/releases).</span><span class="sxs-lookup"><span data-stu-id="281ed-125">Download the packages from [GitHub Release page](https://github.com/PowerShell/PowerShell/releases).</span></span>

<span data-ttu-id="281ed-126">För att distribuera MSI-paketet krävs administratörs behörighet.</span><span class="sxs-lookup"><span data-stu-id="281ed-126">Deploying the MSI package requires Administrator permission.</span></span> <span data-ttu-id="281ed-127">ZIP-paketet kan distribueras av vilken användare som helst.</span><span class="sxs-lookup"><span data-stu-id="281ed-127">The ZIP package can be deployed by any user.</span></span> <span data-ttu-id="281ed-128">ZIP-paketet är det enklaste sättet att installera PowerShell 7 för testning innan du genomför en fullständig installation.</span><span class="sxs-lookup"><span data-stu-id="281ed-128">The ZIP package is the easiest way to install PowerShell 7 for testing, before committing to a full installation.</span></span>

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a><span data-ttu-id="281ed-129">Använda PowerShell 7 sida vid sida med Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="281ed-129">Using PowerShell 7 side-by-side with Windows PowerShell 5.1</span></span>

<span data-ttu-id="281ed-130">PowerShell 7 är utformat för att fungera tillsammans med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="281ed-130">PowerShell 7 is designed to coexist with Windows PowerShell 5.1.</span></span> <span data-ttu-id="281ed-131">Följande funktioner säkerställer att din investering i PowerShell är skyddad och att migreringen till PowerShell 7 är enkel.</span><span class="sxs-lookup"><span data-stu-id="281ed-131">The following features ensure that your investment in PowerShell is protected and your migration to PowerShell 7 is simple.</span></span>

- <span data-ttu-id="281ed-132">Separat installations Sök väg och namn på körbar fil</span><span class="sxs-lookup"><span data-stu-id="281ed-132">Separate installation path and executable name</span></span>
- <span data-ttu-id="281ed-133">Separata PSModulePath</span><span class="sxs-lookup"><span data-stu-id="281ed-133">Separate PSModulePath</span></span>
- <span data-ttu-id="281ed-134">Separata profiler för varje version</span><span class="sxs-lookup"><span data-stu-id="281ed-134">Separate profiles for each version</span></span>
- <span data-ttu-id="281ed-135">Förbättrad modul-kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="281ed-135">Improved module compatibility</span></span>
- <span data-ttu-id="281ed-136">Nya slut punkter för fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="281ed-136">New remoting endpoints</span></span>
- <span data-ttu-id="281ed-137">Stöd för grup princip</span><span class="sxs-lookup"><span data-stu-id="281ed-137">Group policy support</span></span>
- <span data-ttu-id="281ed-138">Separata händelse loggar</span><span class="sxs-lookup"><span data-stu-id="281ed-138">Separate Event logs</span></span>

### <a name="separate-installation-path-and-executable-name"></a><span data-ttu-id="281ed-139">Separat installations Sök väg och namn på körbar fil</span><span class="sxs-lookup"><span data-stu-id="281ed-139">Separate installation path and executable name</span></span>

<span data-ttu-id="281ed-140">PowerShell 7 installeras i en ny katalog, vilket möjliggör körning sida vid sida med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="281ed-140">PowerShell 7 installs to a new directory, enabling side-by-side execution with Windows PowerShell 5.1.</span></span>

<span data-ttu-id="281ed-141">Installera platser efter version:</span><span class="sxs-lookup"><span data-stu-id="281ed-141">Install locations by version:</span></span>

- <span data-ttu-id="281ed-142">Windows PowerShell 5,1:`$env:WINDIR\System32\WindowsPowerShell\v1.0`</span><span class="sxs-lookup"><span data-stu-id="281ed-142">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span></span>
- <span data-ttu-id="281ed-143">PowerShell Core 6. x:`$env:ProgramFiles\PowerShell\6`</span><span class="sxs-lookup"><span data-stu-id="281ed-143">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span></span>
- <span data-ttu-id="281ed-144">PowerShell 7:`$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="281ed-144">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span></span>

<span data-ttu-id="281ed-145">Den nya platsen läggs till i din sökväg så att du kan köra både Windows PowerShell 5,1 och PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="281ed-145">The new location is added to your PATH allowing you to run both Windows PowerShell 5.1 and PowerShell 7.</span></span> <span data-ttu-id="281ed-146">Om du migrerar från PowerShell Core 6. x till PowerShell 7 tas PowerShell 6 bort och sökvägen ersätts.</span><span class="sxs-lookup"><span data-stu-id="281ed-146">If you're migrating from PowerShell Core 6.x to PowerShell 7, PowerShell 6 is removed and the PATH replaced.</span></span>

<span data-ttu-id="281ed-147">I Windows PowerShell heter PowerShell-körbara filen `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="281ed-147">In Windows PowerShell, the PowerShell executable is named `powershell.exe`.</span></span> <span data-ttu-id="281ed-148">I version 6 och senare heter den körbara filen `pwsh.exe` .</span><span class="sxs-lookup"><span data-stu-id="281ed-148">In version 6 and above, the executable is named `pwsh.exe`.</span></span> <span data-ttu-id="281ed-149">Det nya namnet gör det enkelt att stödja körning sida vid sida av båda versionerna.</span><span class="sxs-lookup"><span data-stu-id="281ed-149">The new name makes it easy to support side-by-side execution of both versions.</span></span>

### <a name="separate-psmodulepath"></a><span data-ttu-id="281ed-150">Separata PSModulePath</span><span class="sxs-lookup"><span data-stu-id="281ed-150">Separate PSModulePath</span></span>

<span data-ttu-id="281ed-151">Som standard är Windows PowerShell-och PowerShell 7 Store-moduler på olika platser.</span><span class="sxs-lookup"><span data-stu-id="281ed-151">By default, Windows PowerShell and PowerShell 7 store modules in different locations.</span></span> <span data-ttu-id="281ed-152">PowerShell 7 kombinerar dessa platser i `$Env:PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="281ed-152">PowerShell 7 combines those locations in the `$Env:PSModulePath` environment variable.</span></span> <span data-ttu-id="281ed-153">När du importerar en modul efter namn, kontrollerar PowerShell platsen som anges av `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="281ed-153">When importing a module by name, PowerShell checks the location specified by `$Env:PSModulePath`.</span></span> <span data-ttu-id="281ed-154">Detta gör att PowerShell 7 kan läsa in både Core-och Desktop-moduler.</span><span class="sxs-lookup"><span data-stu-id="281ed-154">This allows PowerShell 7 to load both Core and Desktop modules.</span></span>

|            <span data-ttu-id="281ed-155">Installations omfång</span><span class="sxs-lookup"><span data-stu-id="281ed-155">Install Scope</span></span>            |                <span data-ttu-id="281ed-156">Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="281ed-156">Windows PowerShell 5.1</span></span>                 |             <span data-ttu-id="281ed-157">PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="281ed-157">PowerShell 7.0</span></span>             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="281ed-158">PowerShell-moduler</span><span class="sxs-lookup"><span data-stu-id="281ed-158">PowerShell modules</span></span>                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| <span data-ttu-id="281ed-159">Användaren är installerad</span><span class="sxs-lookup"><span data-stu-id="281ed-159">User installed</span></span><br><span data-ttu-id="281ed-160">AllUsers-omfång</span><span class="sxs-lookup"><span data-stu-id="281ed-160">AllUsers scope</span></span>    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| <span data-ttu-id="281ed-161">Användaren är installerad</span><span class="sxs-lookup"><span data-stu-id="281ed-161">User installed</span></span><br><span data-ttu-id="281ed-162">CurrentUser-omfång</span><span class="sxs-lookup"><span data-stu-id="281ed-162">CurrentUser scope</span></span> | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

<span data-ttu-id="281ed-163">I följande exempel visas standardvärdena för `$Env:PSModulePath` för varje version.</span><span class="sxs-lookup"><span data-stu-id="281ed-163">The following examples show the default values of `$Env:PSModulePath` for each version.</span></span>

- <span data-ttu-id="281ed-164">För Windows PowerShell 5,1:</span><span class="sxs-lookup"><span data-stu-id="281ed-164">For Windows PowerShell 5.1:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- <span data-ttu-id="281ed-165">För PowerShell 7:</span><span class="sxs-lookup"><span data-stu-id="281ed-165">For PowerShell 7:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

<span data-ttu-id="281ed-166">Observera att PowerShell 7 innehåller sökvägar för Windows PowerShell och PowerShell 7-sökvägar för att tillhandahålla automatisk inläsning av moduler.</span><span class="sxs-lookup"><span data-stu-id="281ed-166">Notice that PowerShell 7 includes the Windows PowerShell paths and the PowerShell 7 paths to provide autoloading of modules.</span></span>

> [!NOTE]
> <span data-ttu-id="281ed-167">Det kan finnas ytterligare sökvägar om du har ändrat PSModulePath-miljövariabeln eller installerat anpassade moduler eller program.</span><span class="sxs-lookup"><span data-stu-id="281ed-167">Additional paths may exist if you have changed the PSModulePath environment variable or installed custom modules or applications.</span></span>

<span data-ttu-id="281ed-168">Mer information finns `PSModulePath` i i [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span><span class="sxs-lookup"><span data-stu-id="281ed-168">For more information, see `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span></span>

<span data-ttu-id="281ed-169">Mer information om moduler finns i [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span><span class="sxs-lookup"><span data-stu-id="281ed-169">For more information about Modules, see [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span></span>

### <a name="separate-profiles"></a><span data-ttu-id="281ed-170">Separata profiler</span><span class="sxs-lookup"><span data-stu-id="281ed-170">Separate profiles</span></span>

<span data-ttu-id="281ed-171">En PowerShell-profil är ett skript som körs när PowerShell startar.</span><span class="sxs-lookup"><span data-stu-id="281ed-171">A PowerShell profile is a script that executes when PowerShell starts.</span></span> <span data-ttu-id="281ed-172">Det här skriptet anpassar din miljö genom att lägga till kommandon, alias, funktioner, variabler, moduler och PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="281ed-172">This script customizes your environment by adding commands, aliases, functions, variables, modules, and PowerShell drives.</span></span> <span data-ttu-id="281ed-173">Profil skriptet gör dessa anpassningar tillgängliga i varje session utan att behöva återskapa dem manuellt.</span><span class="sxs-lookup"><span data-stu-id="281ed-173">The profile script makes these customizations available in every session without having to manually recreate them.</span></span>

<span data-ttu-id="281ed-174">Sökvägen till profilens plats har ändrats i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="281ed-174">The path to the location of the profile has changed in PowerShell 7.</span></span>

- <span data-ttu-id="281ed-175">I Windows PowerShell 5,1 är sökvägen till profilen `$HOME\Documents\WindowsPowerShell` .</span><span class="sxs-lookup"><span data-stu-id="281ed-175">In Windows PowerShell 5.1, the location of the profile is `$HOME\Documents\WindowsPowerShell`.</span></span>
- <span data-ttu-id="281ed-176">I PowerShell 7 är platsen för profilen `$HOME\Documents\PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="281ed-176">In PowerShell 7, the location of the profile is `$HOME\Documents\PowerShell`.</span></span>

<span data-ttu-id="281ed-177">Profil fil namnen har också ändrats:</span><span class="sxs-lookup"><span data-stu-id="281ed-177">The profile filenames have also changed:</span></span>

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

<span data-ttu-id="281ed-178">Mer information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="281ed-178">For more information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a><span data-ttu-id="281ed-179">PowerShell 7-kompatibilitet med Windows PowerShell 5,1-moduler</span><span class="sxs-lookup"><span data-stu-id="281ed-179">PowerShell 7 compatibility with Windows PowerShell 5.1 modules</span></span>

<span data-ttu-id="281ed-180">De flesta moduler som du använder i Windows PowerShell 5,1 fungerar redan med PowerShell 7, inklusive Azure PowerShell och Active Directory.</span><span class="sxs-lookup"><span data-stu-id="281ed-180">Most of the modules you use in Windows PowerShell 5.1 already work with PowerShell 7, including Azure PowerShell and Active Directory.</span></span> <span data-ttu-id="281ed-181">Vi fortsätter att arbeta med andra team för att lägga till inbyggt PowerShell 7-stöd för fler moduler, inklusive Microsoft Graph, Office 365 och andra.</span><span class="sxs-lookup"><span data-stu-id="281ed-181">We're continuing to work with other teams to add native PowerShell 7 support for more modules including Microsoft Graph, Office 365, and others.</span></span> <span data-ttu-id="281ed-182">Den aktuella listan över moduler som stöds finns i [PowerShell 7-modulens kompatibilitet](/powershell/scripting/whats-new/module-compatibility).</span><span class="sxs-lookup"><span data-stu-id="281ed-182">For the current list of supported modules, see [PowerShell 7 module compatibility](/powershell/scripting/whats-new/module-compatibility).</span></span>

> [!NOTE]
> <span data-ttu-id="281ed-183">I Windows har vi också lagt till en **UseWindowsPowerShell** -växel för `Import-Module` att under lätta över gången till PowerShell 7 för de som använder inkompatibla moduler.</span><span class="sxs-lookup"><span data-stu-id="281ed-183">On Windows, we've also added a **UseWindowsPowerShell** switch to `Import-Module` to ease the transition to PowerShell 7 for those using incompatible modules.</span></span> <span data-ttu-id="281ed-184">Mer information om den här funktionen finns i [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span><span class="sxs-lookup"><span data-stu-id="281ed-184">For more information on this functionality, see [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span></span>

### <a name="powershell-remoting"></a><span data-ttu-id="281ed-185">PowerShell fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="281ed-185">PowerShell Remoting</span></span>

<span data-ttu-id="281ed-186">Med PowerShell-fjärrkommunikation kan du köra alla PowerShell-kommandon på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="281ed-186">PowerShell remoting lets you run any PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="281ed-187">Du kan upprätta beständiga anslutningar, starta interaktiva sessioner och köra skript på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="281ed-187">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

#### <a name="ws-management-remoting"></a><span data-ttu-id="281ed-188">WS-Management Remoting</span><span class="sxs-lookup"><span data-stu-id="281ed-188">WS-Management remoting</span></span>

<span data-ttu-id="281ed-189">Windows PowerShell 5,1 och tidigare använder WS-Management-protokollet (WSMAN) för anslutnings förhandling och data transport.</span><span class="sxs-lookup"><span data-stu-id="281ed-189">Windows PowerShell 5.1 and below use the WS-Management (WSMAN) protocol for connection negotiation and data transport.</span></span> <span data-ttu-id="281ed-190">Windows Remote Management (WinRM) använder WSMAN-protokollet.</span><span class="sxs-lookup"><span data-stu-id="281ed-190">Windows Remote Management (WinRM) uses the WSMAN protocol.</span></span> <span data-ttu-id="281ed-191">Om WinRM har Aktiver ATS använder PowerShell 7 den befintliga Windows PowerShell 5,1-slutpunkten med namnet `Microsoft.PowerShell` för fjärr anslutningar.</span><span class="sxs-lookup"><span data-stu-id="281ed-191">If WinRM has been enabled, PowerShell 7 uses the existing Windows PowerShell 5.1 endpoint named `Microsoft.PowerShell` for remoting connections.</span></span> <span data-ttu-id="281ed-192">Kör cmdleten om du vill uppdatera PowerShell 7 för att ta med sin egen slut punkt `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="281ed-192">To update PowerShell 7 to include its own endpoint, run the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="281ed-193">Information om hur du ansluter till vissa slut punkter finns i [WS-Management Remoting i PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="281ed-193">For information about connecting to specific endpoints, see [WS-Management Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span></span>

<span data-ttu-id="281ed-194">Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="281ed-194">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="281ed-195">Mer information, inklusive instruktioner, finns i [om krav för fjärrhantering](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="281ed-195">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="281ed-196">Mer information om hur du arbetar med fjärr kommunikation finns i [om fjärran sluten](/powershell/module/microsoft.powershell.core/about/about_remote)</span><span class="sxs-lookup"><span data-stu-id="281ed-196">For more information about working with remoting, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote)</span></span>

#### <a name="ssh-based-remoting"></a><span data-ttu-id="281ed-197">SSH-baserad fjärr kommunikation</span><span class="sxs-lookup"><span data-stu-id="281ed-197">SSH-based remoting</span></span>

<span data-ttu-id="281ed-198">SSH-baserad fjärr kommunikation lades till i PowerShell Core 6. x för att stödja andra operativ system som inte kan använda Windows inbyggda komponenter som **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="281ed-198">SSH-based remoting was added in PowerShell Core 6.x to support other operating systems that can't use Windows native components like **WinRM**.</span></span> <span data-ttu-id="281ed-199">SSH-fjärrkommunikation skapar en PowerShell-värd process på mål datorn som ett SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="281ed-199">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="281ed-200">Mer information och exempel på hur du konfigurerar SSH-baserad fjärr kommunikation i Windows eller Linux finns i: [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="281ed-200">For details and examples on setting up SSH-based remoting on Windows or Linux, see: [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="281ed-201">PowerShell-galleriet (PSGallery) innehåller en modul och en cmdlet som automatiskt konfigurerar SSH-baserad fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="281ed-201">The PowerShell Gallery (PSGallery) contains a module and cmdlet that automatically configures SSH-based remoting.</span></span> <span data-ttu-id="281ed-202">Installera `Microsoft.PowerShell.RemotingTools` modulen från [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) och kör `Enable-SSH` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="281ed-202">Install the `Microsoft.PowerShell.RemotingTools` module from the [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) and run the `Enable-SSH` cmdlet.</span></span>

<span data-ttu-id="281ed-203">`New-PSSession` `Enter-PSSession` Cmdletarna, och `Invoke-Command` har nya parameter uppsättningar som stöder SSH-anslutningar.</span><span class="sxs-lookup"><span data-stu-id="281ed-203">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets have new parameter sets to support SSH connections.</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="281ed-204">Om du vill skapa en fjärrsession anger du mål datorn med parametern **hostname** och anger användar namnet **med användar namnet.**</span><span class="sxs-lookup"><span data-stu-id="281ed-204">To create a remote session, specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="281ed-205">När du kör cmdletarna interaktivt, uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="281ed-205">When running the cmdlets interactively, you're prompted for a password.</span></span>

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

<span data-ttu-id="281ed-206">Om du använder **hostname** -parametern anger du användar namns informationen följt av at-tecknet ( `@` ) följt av dator namnet.</span><span class="sxs-lookup"><span data-stu-id="281ed-206">Alternatively, when using the **HostName** parameter, provide the username information followed by the at sign (`@`), followed by the computer name.</span></span>

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

<span data-ttu-id="281ed-207">Du kan konfigurera SSH-nyckel-autentisering med hjälp av en privat nyckel fil med parametern för nyckel **Sök** vägar.</span><span class="sxs-lookup"><span data-stu-id="281ed-207">You may set up SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span>
<span data-ttu-id="281ed-208">Mer information finns i [openssh Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="281ed-208">For more information, see [OpenSSH Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

### <a name="group-policy-supported"></a><span data-ttu-id="281ed-209">grupprincip som stöds</span><span class="sxs-lookup"><span data-stu-id="281ed-209">Group Policy supported</span></span>

<span data-ttu-id="281ed-210">PowerShell innehåller grupprincip inställningar som hjälper dig att definiera konsekventa alternativ värden för servrar i en företags miljö.</span><span class="sxs-lookup"><span data-stu-id="281ed-210">PowerShell includes Group Policy settings to help you define consistent option values for servers in an enterprise environment.</span></span> <span data-ttu-id="281ed-211">Inställningarna omfattar:</span><span class="sxs-lookup"><span data-stu-id="281ed-211">These settings include:</span></span>

- <span data-ttu-id="281ed-212">Konfiguration av konsolsession: anger en konfigurations slut punkt där PowerShell körs.</span><span class="sxs-lookup"><span data-stu-id="281ed-212">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="281ed-213">Aktivera modul loggning: anger LogPipelineExecutionDetails-egenskapen för moduler.</span><span class="sxs-lookup"><span data-stu-id="281ed-213">Turn on Module Logging: Sets the LogPipelineExecutionDetails property of modules.</span></span>
- <span data-ttu-id="281ed-214">Aktivera loggning av PowerShell-skript block: aktiverar detaljerad loggning av alla PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="281ed-214">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="281ed-215">Aktivera skript körning: ställer in PowerShell-körnings principen.</span><span class="sxs-lookup"><span data-stu-id="281ed-215">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="281ed-216">Aktivera PowerShell-avskrift: aktiverar insamling av indata och utdata från PowerShell-kommandon i textbaserade avskrifter.</span><span class="sxs-lookup"><span data-stu-id="281ed-216">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="281ed-217">Ange standard Sök vägen för uppdatering-hjälp: Anger källan för uppdaterbar hjälp till en katalog, inte Internet.</span><span class="sxs-lookup"><span data-stu-id="281ed-217">Set the default source path for Update-Help: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="281ed-218">Mer information finns i [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span><span class="sxs-lookup"><span data-stu-id="281ed-218">For more information, see [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span></span>

<span data-ttu-id="281ed-219">PowerShell 7 innehåller grupprincip mallar och ett installations skript i `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="281ed-219">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="281ed-220">Grupprincip verktyg använder administrativa mallfiler ( `.admx` , `.adml` ) för att fylla i princip inställningar i användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="281ed-220">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="281ed-221">Detta gör det möjligt för administratörer att hantera registerbaserade princip inställningar.</span><span class="sxs-lookup"><span data-stu-id="281ed-221">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="281ed-222">`InstallPSCorePolicyDefinitions.ps1`Skriptet installerar PowerShell Core administrativa mallar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="281ed-222">The `InstallPSCorePolicyDefinitions.ps1` script installs PowerShell Core Administrative Templates on the local machine.</span></span>

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a><span data-ttu-id="281ed-223">Separata händelse loggar</span><span class="sxs-lookup"><span data-stu-id="281ed-223">Separate Event Logs</span></span>

<span data-ttu-id="281ed-224">Windows PowerShell-och PowerShell 7-logg händelser för att separera händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="281ed-224">Windows PowerShell and PowerShell 7 log events to separate event logs.</span></span> <span data-ttu-id="281ed-225">Använd följande kommando för att hämta en lista över PowerShell-loggar.</span><span class="sxs-lookup"><span data-stu-id="281ed-225">Use the following command to get a list of the PowerShell logs.</span></span>

```powershell
Get-WinEvent -ListLog *PowerShell*
```

<span data-ttu-id="281ed-226">Mer information finns i [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span><span class="sxs-lookup"><span data-stu-id="281ed-226">For more information, see [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span></span>

## <a name="improved-editing-experience-with-visual-studio-code"></a><span data-ttu-id="281ed-227">Förbättrad redigerings upplevelse med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="281ed-227">Improved editing experience with Visual Studio Code</span></span>

<span data-ttu-id="281ed-228">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) med [PowerShell-tillägget](https://code.visualstudio.com/docs/languages/powershell) är den skript miljö som stöds för PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="281ed-228">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) with the [PowerShell Extension](https://code.visualstudio.com/docs/languages/powershell) is the supported scripting environment for PowerShell 7.</span></span> <span data-ttu-id="281ed-229">Windows PowerShell ISE (Integrated Scripting Environment) stöder enbart Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="281ed-229">The Windows PowerShell Integrated Scripting Environment (ISE) only supports Windows PowerShell.</span></span>

<span data-ttu-id="281ed-230">Det uppdaterade PowerShell-tillägget innehåller:</span><span class="sxs-lookup"><span data-stu-id="281ed-230">The updated PowerShell extension includes:</span></span>

- <span data-ttu-id="281ed-231">Nytt ISE-kompatibelt läge</span><span class="sxs-lookup"><span data-stu-id="281ed-231">New ISE compatibility mode</span></span>
- <span data-ttu-id="281ed-232">PSReadLine i den integrerade konsolen, inklusive syntax för syntax, redigering på flera rader och bakåt-sökning</span><span class="sxs-lookup"><span data-stu-id="281ed-232">PSReadLine in the Integrated Console, including syntax highlighting, multi-line editing, and back search</span></span>
- <span data-ttu-id="281ed-233">Stabilitets-och prestanda förbättringar</span><span class="sxs-lookup"><span data-stu-id="281ed-233">Stability and performance improvements</span></span>
- <span data-ttu-id="281ed-234">Ny CodeLens-integrering</span><span class="sxs-lookup"><span data-stu-id="281ed-234">New CodeLens integration</span></span>
- <span data-ttu-id="281ed-235">Förbättrad automatisk komplettering av sökvägen</span><span class="sxs-lookup"><span data-stu-id="281ed-235">Improved path auto-completion</span></span>

<span data-ttu-id="281ed-236">Om du vill göra över gången till Visual Studio Code enklare använder du funktionen **Aktivera ISE-läge** som är tillgänglig i **kommando paletten**.</span><span class="sxs-lookup"><span data-stu-id="281ed-236">To make the transition to Visual Studio Code easier, use the **Enable ISE Mode** function available in the **Command Palette**.</span></span> <span data-ttu-id="281ed-237">Den här funktionen växlar VSCode till en typ av ISE-layout.</span><span class="sxs-lookup"><span data-stu-id="281ed-237">This function switches VSCode into an ISE-style layout.</span></span> <span data-ttu-id="281ed-238">Formatet ISE ger dig alla nya funktioner och funktioner i PowerShell i en välbekant användar upplevelse.</span><span class="sxs-lookup"><span data-stu-id="281ed-238">The ISE-style layout gives you all the new features and capabilities of PowerShell in a familiar user experience.</span></span>

<span data-ttu-id="281ed-239">Du växlar till den nya ISE-layouten genom att trycka på <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> för att öppna **kommando-paletten**, skriva `PowerShell` och välja **PowerShell: Aktivera ISE-läge**.</span><span class="sxs-lookup"><span data-stu-id="281ed-239">To switch to the new ISE layout, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the **Command Palette**, type `PowerShell` and select **PowerShell: Enable ISE Mode**.</span></span>

<span data-ttu-id="281ed-240">Om du vill ställa in layouten på den ursprungliga layouten öppnar du **kommandot palett**, väljer **POWERSHELL: inaktivera ISE-läge (Återställ till standardvärden)**.</span><span class="sxs-lookup"><span data-stu-id="281ed-240">To set the layout to the original layout, open the **Command Palette**, select **PowerShell: Disable ISE Mode (restore to defaults)**.</span></span>

<span data-ttu-id="281ed-241">Mer information om hur du anpassar VSCode-layouten till ISE finns i [så här replikerar du ISE-upplevelsen i Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span><span class="sxs-lookup"><span data-stu-id="281ed-241">For details about customizing the VSCode layout to ISE, see [How to Replicate the ISE Experience in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span></span>

> [!NOTE]
> <span data-ttu-id="281ed-242">Det finns inga planer på att uppdatera ISE med nya funktioner.</span><span class="sxs-lookup"><span data-stu-id="281ed-242">There no plans to update the ISE with new features.</span></span> <span data-ttu-id="281ed-243">ISE är nu en funktion för att avinstallera användare i de senaste versionerna av Windows 10 och Windows Server.</span><span class="sxs-lookup"><span data-stu-id="281ed-243">The ISE is now a user-uninstallable feature in the latest versions of Windows 10 and Windows Server.</span></span> <span data-ttu-id="281ed-244">Det finns inga planer på att permanent ta bort ISE.</span><span class="sxs-lookup"><span data-stu-id="281ed-244">There are no plans to permanently remove the ISE.</span></span> <span data-ttu-id="281ed-245">PowerShell-teamet och dess partners fokuserar på att förbättra skript upplevelsen i PowerShell-tillägget för Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="281ed-245">The PowerShell Team and its partners are focused on improving the scripting experience in the PowerShell extension for Visual Studio Code.</span></span>

## <a name="next-steps"></a><span data-ttu-id="281ed-246">Efterföljande moment</span><span class="sxs-lookup"><span data-stu-id="281ed-246">Next Steps</span></span>

<span data-ttu-id="281ed-247">Följ med kunskapen för att snabbt migrera, [Installera PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) nu!</span><span class="sxs-lookup"><span data-stu-id="281ed-247">Armed with the knowledge to effectively migrate, [install PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) now!</span></span>
