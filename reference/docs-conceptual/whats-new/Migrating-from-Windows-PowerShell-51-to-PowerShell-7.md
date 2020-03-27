---
title: Migrera från Windows PowerShell 5,1 till PowerShell 7
description: Uppdatera från PowerShell 5,1 till PowerShell 7 för dina Windows-plattformar.
ms.date: 03/25/2020
ms.openlocfilehash: e04ab24d2ea94e51f4510d2e96891549c1ede5a4
ms.sourcegitcommit: 7ab6da5169765f06771493b28c44cb24a09d6776
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/26/2020
ms.locfileid: "80296531"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a><span data-ttu-id="182ba-103">Migrera från Windows PowerShell 5,1 till PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="182ba-103">Migrating from Windows PowerShell 5.1 to PowerShell 7</span></span>

<span data-ttu-id="182ba-104">PowerShell 7 är utformat för molnbaserade, lokala miljöer och hybrid miljöer och är förpackat med förbättringar och [nya funktioner](What-s-New-in-PowerShell-70.md).</span><span class="sxs-lookup"><span data-stu-id="182ba-104">Designed for cloud, on-premises, and hybrid environments, PowerShell 7 is packed with enhancements and [new features](What-s-New-in-PowerShell-70.md).</span></span>

- <span data-ttu-id="182ba-105">Installerar och körs sida vid sida med Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="182ba-105">Installs and runs side-by-side with Windows PowerShell</span></span>
- <span data-ttu-id="182ba-106">Förbättrad kompatibilitet med befintliga Windows PowerShell-moduler</span><span class="sxs-lookup"><span data-stu-id="182ba-106">Improved compatibility with existing Windows PowerShell modules</span></span>
- <span data-ttu-id="182ba-107">Nya språk funktioner, som ternär operatörer och `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="182ba-107">New language features, like ternary operators and `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="182ba-108">Bättre prestanda</span><span class="sxs-lookup"><span data-stu-id="182ba-108">Improved performance</span></span>
- <span data-ttu-id="182ba-109">SSH-baserad fjärr kommunikation</span><span class="sxs-lookup"><span data-stu-id="182ba-109">SSH-based remoting</span></span>
- <span data-ttu-id="182ba-110">Samverkan mellan plattformar</span><span class="sxs-lookup"><span data-stu-id="182ba-110">Cross-platform interoperability</span></span>
- <span data-ttu-id="182ba-111">Stöd för Docker-behållare</span><span class="sxs-lookup"><span data-stu-id="182ba-111">Support for Docker containers</span></span>

<span data-ttu-id="182ba-112">PowerShell 7 fungerar sida vid sida med Windows PowerShell och du kan enkelt testa och jämföra versioner innan du distribuerar.</span><span class="sxs-lookup"><span data-stu-id="182ba-112">PowerShell 7 works side-by-side with Windows PowerShell letting you easily test and compare between editions before deployment.</span></span> <span data-ttu-id="182ba-113">Migrering är enkel, snabb och säker.</span><span class="sxs-lookup"><span data-stu-id="182ba-113">Migration is simple, quick, and safe.</span></span> <span data-ttu-id="182ba-114">haverera.</span><span class="sxs-lookup"><span data-stu-id="182ba-114">failure.</span></span>

<span data-ttu-id="182ba-115">PowerShell 7 stöds i följande Windows-operativ system:</span><span class="sxs-lookup"><span data-stu-id="182ba-115">PowerShell 7 is supported on the following Windows operating systems:</span></span>

- <span data-ttu-id="182ba-116">Windows 8,1 och 10</span><span class="sxs-lookup"><span data-stu-id="182ba-116">Windows 8.1 and 10</span></span>
- <span data-ttu-id="182ba-117">Windows Server 2012, 2012 R2, 2016 och 2019</span><span class="sxs-lookup"><span data-stu-id="182ba-117">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>

<span data-ttu-id="182ba-118">PowerShell 7 körs också på macOS och flera Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="182ba-118">PowerShell 7 also runs on macOS and several Linux distributions.</span></span> <span data-ttu-id="182ba-119">En lista över operativ system som stöds och information om support livs cykeln finns i [PowerShell-Supportens livs cykel](/powershell/scripting/powershell-support-lifecycle).</span><span class="sxs-lookup"><span data-stu-id="182ba-119">For a list of supported operating systems and information about the support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="installing-powershell-7"></a><span data-ttu-id="182ba-120">Installera PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="182ba-120">Installing PowerShell 7</span></span>

<span data-ttu-id="182ba-121">Det finns flera tillgängliga alternativ för att installera PowerShell 7 för flexibilitet och för att stödja behoven hos IT, DevOps-tekniker och utvecklare.</span><span class="sxs-lookup"><span data-stu-id="182ba-121">For flexibility and to support the needs of IT, DevOps engineers, and developers, there are several options available to install PowerShell 7.</span></span> <span data-ttu-id="182ba-122">I de flesta fall kan installations alternativen minskas till följande metoder:</span><span class="sxs-lookup"><span data-stu-id="182ba-122">In most cases, the installation options can be reduced to the following methods:</span></span>

- <span data-ttu-id="182ba-123">Distribuera PowerShell med [MSI-paketet](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span><span class="sxs-lookup"><span data-stu-id="182ba-123">Deploy PowerShell using the [MSI package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span></span>
- <span data-ttu-id="182ba-124">Distribuera PowerShell med [zip-paketet](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span><span class="sxs-lookup"><span data-stu-id="182ba-124">Deploy PowerShell using the [ZIP package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span></span>

> [!NOTE]
> <span data-ttu-id="182ba-125">MSI-paketet kan distribueras och uppdateras med hanterings produkter som [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span><span class="sxs-lookup"><span data-stu-id="182ba-125">The MSI package can be deployed and updated with management products such as [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span></span> <span data-ttu-id="182ba-126">Hämta paketen från [GitHub release-sidan](https://github.com/PowerShell/PowerShell/releases).</span><span class="sxs-lookup"><span data-stu-id="182ba-126">Download the packages from [GitHub Release page](https://github.com/PowerShell/PowerShell/releases).</span></span>

<span data-ttu-id="182ba-127">För att distribuera MSI-paketet krävs administratörs behörighet.</span><span class="sxs-lookup"><span data-stu-id="182ba-127">Deploying the MSI package requires Administrator permission.</span></span> <span data-ttu-id="182ba-128">ZIP-paketet kan distribueras av vilken användare som helst.</span><span class="sxs-lookup"><span data-stu-id="182ba-128">The ZIP package can be deployed by any user.</span></span> <span data-ttu-id="182ba-129">ZIP-paketet är det enklaste sättet att installera PowerShell 7 för testning innan du genomför en fullständig installation.</span><span class="sxs-lookup"><span data-stu-id="182ba-129">The ZIP package is the easiest way to install PowerShell 7 for testing, before committing to a full installation.</span></span>

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a><span data-ttu-id="182ba-130">Använda PowerShell 7 sida vid sida med Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="182ba-130">Using PowerShell 7 side-by-side with Windows PowerShell 5.1</span></span>

<span data-ttu-id="182ba-131">PowerShell 7 är utformat för att fungera tillsammans med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="182ba-131">PowerShell 7 is designed to coexist with Windows PowerShell 5.1.</span></span> <span data-ttu-id="182ba-132">Följande funktioner säkerställer att din investering i PowerShell är skyddad och att migreringen till PowerShell 7 är enkel.</span><span class="sxs-lookup"><span data-stu-id="182ba-132">The following features ensure that your investment in PowerShell is protected and your migration to PowerShell 7 is simple.</span></span>

- <span data-ttu-id="182ba-133">Separat installations Sök väg och namn på körbar fil</span><span class="sxs-lookup"><span data-stu-id="182ba-133">Separate installation path and executable name</span></span>
- <span data-ttu-id="182ba-134">Separata PSModulePath</span><span class="sxs-lookup"><span data-stu-id="182ba-134">Separate PSModulePath</span></span>
- <span data-ttu-id="182ba-135">Separata profiler för varje version</span><span class="sxs-lookup"><span data-stu-id="182ba-135">Separate profiles for each version</span></span>
- <span data-ttu-id="182ba-136">Förbättrad modul-kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="182ba-136">Improved module compatibility</span></span>
- <span data-ttu-id="182ba-137">Nya slut punkter för fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="182ba-137">New remoting endpoints</span></span>
- <span data-ttu-id="182ba-138">Stöd för grup princip</span><span class="sxs-lookup"><span data-stu-id="182ba-138">Group policy support</span></span>
- <span data-ttu-id="182ba-139">Separata händelse loggar</span><span class="sxs-lookup"><span data-stu-id="182ba-139">Separate Event logs</span></span>

### <a name="separate-installation-path-and-executable-name"></a><span data-ttu-id="182ba-140">Separat installations Sök väg och namn på körbar fil</span><span class="sxs-lookup"><span data-stu-id="182ba-140">Separate installation path and executable name</span></span>

<span data-ttu-id="182ba-141">PowerShell 7 installeras i en ny katalog, vilket möjliggör körning sida vid sida med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="182ba-141">PowerShell 7 installs to a new directory, enabling side-by-side execution with Windows PowerShell 5.1.</span></span>

<span data-ttu-id="182ba-142">Installera platser efter version:</span><span class="sxs-lookup"><span data-stu-id="182ba-142">Install locations by version:</span></span>

- <span data-ttu-id="182ba-143">Windows PowerShell 5,1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span><span class="sxs-lookup"><span data-stu-id="182ba-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span></span>
- <span data-ttu-id="182ba-144">PowerShell Core 6. x: `$env:ProgramFiles\PowerShell\6`</span><span class="sxs-lookup"><span data-stu-id="182ba-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span></span>
- <span data-ttu-id="182ba-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="182ba-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span></span>

<span data-ttu-id="182ba-146">Den nya platsen läggs till i din sökväg så att du kan köra både Windows PowerShell 5,1 och PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="182ba-146">The new location is added to your PATH allowing you to run both Windows PowerShell 5.1 and PowerShell 7.</span></span> <span data-ttu-id="182ba-147">Om du migrerar från PowerShell Core 6. x till PowerShell 7 tas PowerShell 6 bort och sökvägen ersätts.</span><span class="sxs-lookup"><span data-stu-id="182ba-147">If you're migrating from PowerShell Core 6.x to PowerShell 7, PowerShell 6 is removed and the PATH replaced.</span></span>

<span data-ttu-id="182ba-148">I Windows PowerShell heter PowerShell-körbaren `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="182ba-148">In Windows PowerShell, the PowerShell executable is named `powershell.exe`.</span></span> <span data-ttu-id="182ba-149">I version 6 och senare heter den körbara filen `pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="182ba-149">In version 6 and above, the executable is named `pwsh.exe`.</span></span> <span data-ttu-id="182ba-150">Det nya namnet gör det enkelt att stödja körning sida vid sida av båda versionerna.</span><span class="sxs-lookup"><span data-stu-id="182ba-150">The new name makes it easy to support side-by-side execution of both versions.</span></span>

### <a name="separate-psmodulepath"></a><span data-ttu-id="182ba-151">Separata PSModulePath</span><span class="sxs-lookup"><span data-stu-id="182ba-151">Separate PSModulePath</span></span>

<span data-ttu-id="182ba-152">Som standard är Windows PowerShell-och PowerShell 7 Store-moduler på olika platser.</span><span class="sxs-lookup"><span data-stu-id="182ba-152">By default, Windows PowerShell and PowerShell 7 store modules in different locations.</span></span> <span data-ttu-id="182ba-153">PowerShell 7 kombinerar dessa platser i `$Env:PSModulePath`-miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="182ba-153">PowerShell 7 combines those locations in the `$Env:PSModulePath` environment variable.</span></span> <span data-ttu-id="182ba-154">När du importerar en modul efter namn, kontrollerar PowerShell platsen som anges av `$Env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="182ba-154">When importing a module by name, PowerShell checks the location specified by `$Env:PSModulePath`.</span></span> <span data-ttu-id="182ba-155">Detta gör att PowerShell 7 kan läsa in både Core-och Desktop-moduler.</span><span class="sxs-lookup"><span data-stu-id="182ba-155">This allows PowerShell 7 to load both Core and Desktop modules.</span></span>

|            <span data-ttu-id="182ba-156">Installations omfång</span><span class="sxs-lookup"><span data-stu-id="182ba-156">Install Scope</span></span>            |                <span data-ttu-id="182ba-157">Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="182ba-157">Windows PowerShell 5.1</span></span>                 |             <span data-ttu-id="182ba-158">PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="182ba-158">PowerShell 7.0</span></span>             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="182ba-159">PowerShell-moduler</span><span class="sxs-lookup"><span data-stu-id="182ba-159">PowerShell modules</span></span>                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| <span data-ttu-id="182ba-160">Användaren är installerad</span><span class="sxs-lookup"><span data-stu-id="182ba-160">User installed</span></span><br><span data-ttu-id="182ba-161">AllUsers-omfång</span><span class="sxs-lookup"><span data-stu-id="182ba-161">AllUsers scope</span></span>    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| <span data-ttu-id="182ba-162">Användaren är installerad</span><span class="sxs-lookup"><span data-stu-id="182ba-162">User installed</span></span><br><span data-ttu-id="182ba-163">CurrentUser-omfång</span><span class="sxs-lookup"><span data-stu-id="182ba-163">CurrentUser scope</span></span> | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

<span data-ttu-id="182ba-164">I följande exempel visas standardvärdena för `$Env:PSModulePath` för varje version.</span><span class="sxs-lookup"><span data-stu-id="182ba-164">The following examples show the default values of `$Env:PSModulePath` for each version.</span></span>

- <span data-ttu-id="182ba-165">För Windows PowerShell 5,1:</span><span class="sxs-lookup"><span data-stu-id="182ba-165">For Windows PowerShell 5.1:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- <span data-ttu-id="182ba-166">För PowerShell 7:</span><span class="sxs-lookup"><span data-stu-id="182ba-166">For PowerShell 7:</span></span>

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

<span data-ttu-id="182ba-167">Observera att PowerShell 7 innehåller sökvägar för Windows PowerShell och PowerShell 7-sökvägar för att tillhandahålla automatisk inläsning av moduler.</span><span class="sxs-lookup"><span data-stu-id="182ba-167">Notice that PowerShell 7 includes the Windows PowerShell paths and the PowerShell 7 paths to provide autoloading of modules.</span></span>

> [!NOTE]
> <span data-ttu-id="182ba-168">Det kan finnas ytterligare sökvägar om du har ändrat PSModulePath-miljövariabeln eller installerat anpassade moduler eller program.</span><span class="sxs-lookup"><span data-stu-id="182ba-168">Additional paths may exist if you have changed the PSModulePath environment variable or installed custom modules or applications.</span></span>

<span data-ttu-id="182ba-169">Mer information finns i `PSModulePath` i [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span><span class="sxs-lookup"><span data-stu-id="182ba-169">For more information, see `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span></span>

<span data-ttu-id="182ba-170">Mer information om moduler finns i [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span><span class="sxs-lookup"><span data-stu-id="182ba-170">For more information about Modules, see [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span></span>

### <a name="separate-profiles"></a><span data-ttu-id="182ba-171">Separata profiler</span><span class="sxs-lookup"><span data-stu-id="182ba-171">Separate profiles</span></span>

<span data-ttu-id="182ba-172">En PowerShell-profil är ett skript som körs när PowerShell startar.</span><span class="sxs-lookup"><span data-stu-id="182ba-172">A PowerShell profile is a script that executes when PowerShell starts.</span></span> <span data-ttu-id="182ba-173">Det här skriptet anpassar din miljö genom att lägga till kommandon, alias, funktioner, variabler, moduler och PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="182ba-173">This script customizes your environment by adding commands, aliases, functions, variables, modules, and PowerShell drives.</span></span> <span data-ttu-id="182ba-174">Profil skriptet gör dessa anpassningar tillgängliga i varje session utan att behöva återskapa dem manuellt.</span><span class="sxs-lookup"><span data-stu-id="182ba-174">The profile script makes these customizations available in every session without having to manually recreate them.</span></span>

<span data-ttu-id="182ba-175">Sökvägen till profilens plats har ändrats i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="182ba-175">The path to the location of the profile has changed in PowerShell 7.</span></span>

- <span data-ttu-id="182ba-176">I Windows PowerShell 5,1 är sökvägen till profilen `$HOME\Documents\WindowsPowerShell`.</span><span class="sxs-lookup"><span data-stu-id="182ba-176">In Windows PowerShell 5.1, the location of the profile is `$HOME\Documents\WindowsPowerShell`.</span></span>
- <span data-ttu-id="182ba-177">I PowerShell 7 är platsen för profilen `$HOME\Documents\PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="182ba-177">In PowerShell 7, the location of the profile is `$HOME\Documents\PowerShell`.</span></span>

<span data-ttu-id="182ba-178">Profil fil namnen har också ändrats:</span><span class="sxs-lookup"><span data-stu-id="182ba-178">The profile filenames have also changed:</span></span>

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

<span data-ttu-id="182ba-179">Mer information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="182ba-179">For more information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a><span data-ttu-id="182ba-180">PowerShell 7-kompatibilitet med Windows PowerShell 5,1-moduler</span><span class="sxs-lookup"><span data-stu-id="182ba-180">PowerShell 7 compatibility with Windows PowerShell 5.1 modules</span></span>

<span data-ttu-id="182ba-181">De flesta moduler som du använder i Windows PowerShell 5,1 fungerar redan med PowerShell 7, inklusive Azure PowerShell och Active Directory.</span><span class="sxs-lookup"><span data-stu-id="182ba-181">Most of the modules you use in Windows PowerShell 5.1 already work with PowerShell 7, including Azure PowerShell and Active Directory.</span></span> <span data-ttu-id="182ba-182">Vi fortsätter att arbeta med andra team för att lägga till inbyggt PowerShell 7-stöd för fler moduler, inklusive Microsoft Graph, Office 365 och andra.</span><span class="sxs-lookup"><span data-stu-id="182ba-182">We're continuing to work with other teams to add native PowerShell 7 support for more modules including Microsoft Graph, Office 365, and others.</span></span> <span data-ttu-id="182ba-183">Den aktuella listan över moduler som stöds finns i [PowerShell 7-modulens kompatibilitet](/powershell/scripting/whats-new/module-compatibility).</span><span class="sxs-lookup"><span data-stu-id="182ba-183">For the current list of supported modules, see [PowerShell 7 module compatibility](/powershell/scripting/whats-new/module-compatibility).</span></span>

[!NOTE]
> <span data-ttu-id="182ba-184">I Windows har vi också lagt till en **UseWindowsPowerShell** -växel till `Import-Module` för att under lätta över gången till PowerShell 7 för de som använder inkompatibla moduler.</span><span class="sxs-lookup"><span data-stu-id="182ba-184">On Windows, we've also added a **UseWindowsPowerShell** switch to `Import-Module` to ease the transition to PowerShell 7 for those using incompatible modules.</span></span> <span data-ttu-id="182ba-185">Mer information om den här funktionen finns i [about_Windows_PowerShell_Compatibility](/powershell/modules/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span><span class="sxs-lookup"><span data-stu-id="182ba-185">For more information on this functionality, see [about_Windows_PowerShell_Compatibility](/powershell/modules/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span></span>

### <a name="powershell-remoting"></a><span data-ttu-id="182ba-186">PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="182ba-186">PowerShell Remoting</span></span>

<span data-ttu-id="182ba-187">Med PowerShell-fjärrkommunikation kan du köra alla PowerShell-kommandon på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="182ba-187">PowerShell remoting lets you run any PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="182ba-188">Du kan upprätta beständiga anslutningar, starta interaktiva sessioner och köra skript på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="182ba-188">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

#### <a name="ws-management-remoting"></a><span data-ttu-id="182ba-189">WS-Management Remoting</span><span class="sxs-lookup"><span data-stu-id="182ba-189">WS-Management remoting</span></span>

<span data-ttu-id="182ba-190">Windows PowerShell 5,1 och tidigare använder WS-Management-protokollet (WSMAN) för anslutnings förhandling och data transport.</span><span class="sxs-lookup"><span data-stu-id="182ba-190">Windows PowerShell 5.1 and below use the WS-Management (WSMAN) protocol for connection negotiation and data transport.</span></span> <span data-ttu-id="182ba-191">Windows Remote Management (WinRM) använder WSMAN-protokollet.</span><span class="sxs-lookup"><span data-stu-id="182ba-191">Windows Remote Management (WinRM) uses the WSMAN protocol.</span></span> <span data-ttu-id="182ba-192">Om WinRM har Aktiver ATS använder PowerShell 7 den befintliga Windows PowerShell 5,1-slutpunkten med namnet `Microsoft.PowerShell` för fjärr anslutningar.</span><span class="sxs-lookup"><span data-stu-id="182ba-192">If WinRM has been enabled, PowerShell 7 uses the existing Windows PowerShell 5.1 endpoint named `Microsoft.PowerShell` for remoting connections.</span></span> <span data-ttu-id="182ba-193">Kör cmdleten `Enable-PSRemoting` om du vill uppdatera PowerShell 7 för att ta med sin egen slut punkt.</span><span class="sxs-lookup"><span data-stu-id="182ba-193">To update PowerShell 7 to include its own endpoint, run the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="182ba-194">Information om hur du ansluter till vissa slut punkter finns i [WS-Management Remoting i PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="182ba-194">For information about connecting to specific endpoints, see [WS-Management Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span></span>

<span data-ttu-id="182ba-195">Om du vill använda Windows PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="182ba-195">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="182ba-196">Mer information, inklusive instruktioner, finns i [om krav för fjärrhantering](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="182ba-196">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="182ba-197">Mer information om hur du arbetar med fjärr kommunikation finns i [om fjärran sluten](/powershell/module/microsoft.powershell.core/about/about_remote)</span><span class="sxs-lookup"><span data-stu-id="182ba-197">For more information about working with remoting, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote)</span></span>

#### <a name="ssh-based-remoting"></a><span data-ttu-id="182ba-198">SSH-baserad fjärr kommunikation</span><span class="sxs-lookup"><span data-stu-id="182ba-198">SSH-based remoting</span></span>

<span data-ttu-id="182ba-199">SSH-baserad fjärr kommunikation lades till i PowerShell Core 6. x för att stödja andra operativ system som inte kan använda Windows inbyggda komponenter som **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="182ba-199">SSH-based remoting was added in PowerShell Core 6.x to support other operating systems that can't use Windows native components like **WinRM**.</span></span> <span data-ttu-id="182ba-200">SSH-fjärrkommunikation skapar en PowerShell-värd process på mål datorn som ett SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="182ba-200">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="182ba-201">Mer information och exempel på hur du konfigurerar SSH-baserad fjärr kommunikation i Windows eller Linux finns i: [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="182ba-201">For details and examples on setting up SSH-based remoting on Windows or Linux, see: [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="182ba-202">PowerShell-galleriet (PSGallery) innehåller en modul och en cmdlet som automatiskt konfigurerar SSH-baserad fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="182ba-202">The PowerShell Gallery (PSGallery) contains a module and cmdlet that automatically configures SSH-based remoting.</span></span> <span data-ttu-id="182ba-203">Installera `Microsoft.PowerShell.RemotingTools`-modulen från [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) och kör `Enable-SSH`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="182ba-203">Install the `Microsoft.PowerShell.RemotingTools` module from the [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) and run the `Enable-SSH` cmdlet.</span></span>

<span data-ttu-id="182ba-204">Cmdletarna `New-PSSession`, `Enter-PSSession`och `Invoke-Command` har nya parameter uppsättningar som stöder SSH-anslutningar.</span><span class="sxs-lookup"><span data-stu-id="182ba-204">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets have new parameter sets to support SSH connections.</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="182ba-205">Om du vill skapa en fjärrsession anger du mål datorn med parametern **hostname** och anger användar namnet **med användar namnet.**</span><span class="sxs-lookup"><span data-stu-id="182ba-205">To create a remote session, specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="182ba-206">När du kör cmdletarna interaktivt, uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="182ba-206">When running the cmdlets interactively, you're prompted for a password.</span></span>

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

<span data-ttu-id="182ba-207">Om du använder **hostname** -parametern anger du användar namns informationen följt av at-tecknet (@) följt av dator namnet.</span><span class="sxs-lookup"><span data-stu-id="182ba-207">Alternatively, when using the **HostName** parameter, provide the username information followed by the at sign ('@'), followed by the computer name.</span></span>

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

<span data-ttu-id="182ba-208">Du kan konfigurera SSH-nyckel-autentisering med hjälp av en privat nyckel fil med parametern för nyckel **Sök** vägar.</span><span class="sxs-lookup"><span data-stu-id="182ba-208">You may set up SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span>
<span data-ttu-id="182ba-209">Mer information finns i [openssh Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="182ba-209">For more information, see [OpenSSH Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

### <a name="group-policy-supported"></a><span data-ttu-id="182ba-210">grupprincip som stöds</span><span class="sxs-lookup"><span data-stu-id="182ba-210">Group Policy supported</span></span>

<span data-ttu-id="182ba-211">PowerShell innehåller grupprincip inställningar som hjälper dig att definiera konsekventa alternativ värden för servrar i en företags miljö.</span><span class="sxs-lookup"><span data-stu-id="182ba-211">PowerShell includes Group Policy settings to help you define consistent option values for servers in an enterprise environment.</span></span> <span data-ttu-id="182ba-212">Inställningarna omfattar:</span><span class="sxs-lookup"><span data-stu-id="182ba-212">These settings include:</span></span>

- <span data-ttu-id="182ba-213">Konfiguration av konsolsession: anger en konfigurations slut punkt där PowerShell körs.</span><span class="sxs-lookup"><span data-stu-id="182ba-213">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="182ba-214">Aktivera modul loggning: anger LogPipelineExecutionDetails-egenskapen för moduler.</span><span class="sxs-lookup"><span data-stu-id="182ba-214">Turn on Module Logging: Sets the LogPipelineExecutionDetails property of modules.</span></span>
- <span data-ttu-id="182ba-215">Aktivera loggning av PowerShell-skript block: aktiverar detaljerad loggning av alla PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="182ba-215">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="182ba-216">Aktivera skript körning: ställer in PowerShell-körnings principen.</span><span class="sxs-lookup"><span data-stu-id="182ba-216">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="182ba-217">Aktivera PowerShell-avskrift: aktiverar insamling av indata och utdata från PowerShell-kommandon i textbaserade avskrifter.</span><span class="sxs-lookup"><span data-stu-id="182ba-217">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="182ba-218">Ange standard Sök vägen för uppdatering-hjälp: Anger källan för uppdaterbar hjälp till en katalog, inte Internet.</span><span class="sxs-lookup"><span data-stu-id="182ba-218">Set the default source path for Update-Help: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="182ba-219">Mer information finns i [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span><span class="sxs-lookup"><span data-stu-id="182ba-219">For more information, see [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span></span>

<span data-ttu-id="182ba-220">PowerShell 7 innehåller grupprincip mallar och ett installations skript i `$PSHOME`.</span><span class="sxs-lookup"><span data-stu-id="182ba-220">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="182ba-221">Grupprincip verktyg använder administrativa mallfiler (`.admx`, `.adml`) för att fylla i princip inställningar i användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="182ba-221">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="182ba-222">Detta gör det möjligt för administratörer att hantera registerbaserade princip inställningar.</span><span class="sxs-lookup"><span data-stu-id="182ba-222">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="182ba-223">`InstallPSCorePolicyDefinitions.ps1` skriptet installerar PowerShell Core Administrativa mallar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="182ba-223">The `InstallPSCorePolicyDefinitions.ps1` script installs PowerShell Core Administrative Templates on the local machine.</span></span>

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

### <a name="separate-event-logs"></a><span data-ttu-id="182ba-224">Separata händelse loggar</span><span class="sxs-lookup"><span data-stu-id="182ba-224">Separate Event Logs</span></span>

<span data-ttu-id="182ba-225">Windows PowerShell-och PowerShell 7-logg händelser för att separera händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="182ba-225">Windows PowerShell and PowerShell 7 log events to separate event logs.</span></span> <span data-ttu-id="182ba-226">Använd följande kommando för att hämta en lista över PowerShell-loggar.</span><span class="sxs-lookup"><span data-stu-id="182ba-226">Use the following command to get a list of the PowerShell logs.</span></span>

```powershell
Get-WinEvent -ListLog *PowerShell*
```

<span data-ttu-id="182ba-227">Mer information finns i [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span><span class="sxs-lookup"><span data-stu-id="182ba-227">For more information, see [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span></span>

## <a name="improved-editing-experience-with-visual-studio-code"></a><span data-ttu-id="182ba-228">Förbättrad redigerings upplevelse med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="182ba-228">Improved editing experience with Visual Studio Code</span></span>

<span data-ttu-id="182ba-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) med [PowerShell-tillägget](https://code.visualstudio.com/docs/languages/powershell) är den skript miljö som stöds för PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="182ba-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) with the [PowerShell Extension](https://code.visualstudio.com/docs/languages/powershell) is the supported scripting environment for PowerShell 7.</span></span> <span data-ttu-id="182ba-230">Windows PowerShell ISE (Integrated Scripting Environment) stöder enbart Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="182ba-230">The Windows PowerShell Integrated Scripting Environment (ISE) only supports Windows PowerShell.</span></span>

<span data-ttu-id="182ba-231">Det uppdaterade PowerShell-tillägget innehåller:</span><span class="sxs-lookup"><span data-stu-id="182ba-231">The updated PowerShell extension includes:</span></span>

- <span data-ttu-id="182ba-232">Nytt ISE-kompatibelt läge</span><span class="sxs-lookup"><span data-stu-id="182ba-232">New ISE compatibility mode</span></span>
- <span data-ttu-id="182ba-233">PSReadLine i den integrerade konsolen, inklusive syntax för syntax, redigering på flera rader och bakåt-sökning</span><span class="sxs-lookup"><span data-stu-id="182ba-233">PSReadLine in the Integrated Console, including syntax highlighting, multi-line editing, and back search</span></span>
- <span data-ttu-id="182ba-234">Stabilitets-och prestanda förbättringar</span><span class="sxs-lookup"><span data-stu-id="182ba-234">Stability and performance improvements</span></span>
- <span data-ttu-id="182ba-235">Ny CodeLens-integrering</span><span class="sxs-lookup"><span data-stu-id="182ba-235">New CodeLens integration</span></span>
- <span data-ttu-id="182ba-236">Förbättrad automatisk komplettering av sökvägen</span><span class="sxs-lookup"><span data-stu-id="182ba-236">Improved path auto-completion</span></span>

<span data-ttu-id="182ba-237">Om du vill göra över gången till Visual Studio Code enklare använder du funktionen **Aktivera ISE-läge** som är tillgänglig i **kommando paletten**.</span><span class="sxs-lookup"><span data-stu-id="182ba-237">To make the transition to Visual Studio Code easier, use the **Enable ISE Mode** function available in the **Command Palette**.</span></span> <span data-ttu-id="182ba-238">Den här funktionen växlar VSCode till en typ av ISE-layout.</span><span class="sxs-lookup"><span data-stu-id="182ba-238">This function switches VSCode into an ISE-style layout.</span></span> <span data-ttu-id="182ba-239">Formatet ISE ger dig alla nya funktioner och funktioner i PowerShell i en välbekant användar upplevelse.</span><span class="sxs-lookup"><span data-stu-id="182ba-239">The ISE-style layout gives you all the new features and capabilities of PowerShell in a familiar user experience.</span></span>

<span data-ttu-id="182ba-240">Om du vill växla till den nya ISE-layouten trycker du på <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> för att öppna **kommando-paletten**, skriv `PowerShell` och välj **PowerShell: Aktivera ISE-läge**.</span><span class="sxs-lookup"><span data-stu-id="182ba-240">To switch to the new ISE layout, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the **Command Palette**, type `PowerShell` and select **PowerShell: Enable ISE Mode**.</span></span>

<span data-ttu-id="182ba-241">Om du vill ställa in layouten på den ursprungliga layouten öppnar du **kommandot palett**, väljer **POWERSHELL: inaktivera ISE-läge (Återställ till standardvärden)** .</span><span class="sxs-lookup"><span data-stu-id="182ba-241">To set the layout to the original layout, open the **Command Palette**, select **PowerShell: Disable ISE Mode (restore to defaults)**.</span></span>

<span data-ttu-id="182ba-242">Mer information om hur du anpassar VSCode-layouten till ISE finns i [så här replikerar du ISE-upplevelsen i Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span><span class="sxs-lookup"><span data-stu-id="182ba-242">For details about customizing the VSCode layout to ISE, see [How to Replicate the ISE Experience in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span></span>

> [!NOTE]
> <span data-ttu-id="182ba-243">Det finns inga planer på att uppdatera ISE med nya funktioner.</span><span class="sxs-lookup"><span data-stu-id="182ba-243">There no plans to update the ISE with new features.</span></span> <span data-ttu-id="182ba-244">ISE är nu en funktion för att avinstallera användare i de senaste versionerna av Windows 10 och Windows Server.</span><span class="sxs-lookup"><span data-stu-id="182ba-244">The ISE is now a user-uninstallable feature in the latest versions of Windows 10 and Windows Server.</span></span> <span data-ttu-id="182ba-245">Det finns inga planer på att permanent ta bort ISE.</span><span class="sxs-lookup"><span data-stu-id="182ba-245">There are no plans to permanently remove the ISE.</span></span> <span data-ttu-id="182ba-246">PowerShell-teamet och dess partners fokuserar på att förbättra skript upplevelsen i PowerShell-tillägget för Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="182ba-246">The PowerShell Team and its partners are focused on improving the scripting experience in the PowerShell extension for Visual Studio Code.</span></span>

## <a name="next-steps"></a><span data-ttu-id="182ba-247">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="182ba-247">Next Steps</span></span>

<span data-ttu-id="182ba-248">Följ med kunskapen för att snabbt migrera, [Installera PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) nu!</span><span class="sxs-lookup"><span data-stu-id="182ba-248">Armed with the knowledge to effectively migrate, [install PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) now!</span></span>
