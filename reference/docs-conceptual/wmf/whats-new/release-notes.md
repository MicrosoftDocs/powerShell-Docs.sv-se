---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Versionsinformation för WMF 5.x
ms.openlocfilehash: 3fc712dbcbe184c60ae248b260c8f6800f111fdd
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79406848"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="21fd1-103">Viktig information om Windows Management Framework (WMF) 5. x</span><span class="sxs-lookup"><span data-stu-id="21fd1-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="21fd1-104">WMF 5,0-ändringar</span><span class="sxs-lookup"><span data-stu-id="21fd1-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="21fd1-105">PowerShell 5,0 lägger till en ny strukturerad **informations** ström</span><span class="sxs-lookup"><span data-stu-id="21fd1-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="21fd1-106">Förbättringar av DSC, inklusive fyra nya DSC-resurser:</span><span class="sxs-lookup"><span data-stu-id="21fd1-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="21fd1-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="21fd1-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="21fd1-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="21fd1-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="21fd1-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="21fd1-109">ServiceSet</span></span>
  - <span data-ttu-id="21fd1-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="21fd1-110">ProcessSet</span></span>
- <span data-ttu-id="21fd1-111">Lade till bara tillräckligt med administration för att aktivera rollbaserad administration via PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="21fd1-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="21fd1-112">PowerShell 5,0 utökar språket till att inkludera användardefinierade klasser och uppräkningar</span><span class="sxs-lookup"><span data-stu-id="21fd1-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="21fd1-113">Förbättrade fel söknings funktioner i PowerShell ISE och ytterligare fjärrfelsökning</span><span class="sxs-lookup"><span data-stu-id="21fd1-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="21fd1-114">PowerShellGet-och PackageManagement-modulerna har lagts till</span><span class="sxs-lookup"><span data-stu-id="21fd1-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="21fd1-115">Förbättrat PowerShell-skript, loggning och avskrifter</span><span class="sxs-lookup"><span data-stu-id="21fd1-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="21fd1-116">Lägg till cmdletar för kryptografiskt meddelande-syntax</span><span class="sxs-lookup"><span data-stu-id="21fd1-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="21fd1-117">WMF 5,0 innehåller NetworkSwitchManager-modulen för Windows</span><span class="sxs-lookup"><span data-stu-id="21fd1-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="21fd1-118">Modulen Microsoft. PowerShell. ODataUtils har lagts till</span><span class="sxs-lookup"><span data-stu-id="21fd1-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="21fd1-119">Stöd för Software Inventory Logging (SIL) har lagts till</span><span class="sxs-lookup"><span data-stu-id="21fd1-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="21fd1-120">Sever New eller Update-cmdletar som svar på användar förfrågningar och problem</span><span class="sxs-lookup"><span data-stu-id="21fd1-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="21fd1-121">WMF 5,1-ändringar</span><span class="sxs-lookup"><span data-stu-id="21fd1-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="21fd1-122">WMF 5,1 innehåller komponenterna PowerShell, WMI, WinRM och Software Inventory Logging (SIL) som släpptes med Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="21fd1-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="21fd1-123">WMF 5,1 kan installeras på Windows 7, Windows 8,1, Windows Server 2008 R2, 2012 och 2012 R2, och innehåller flera förbättringar över WMF 5,0, inklusive:</span><span class="sxs-lookup"><span data-stu-id="21fd1-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="21fd1-124">Nya cmdletar</span><span class="sxs-lookup"><span data-stu-id="21fd1-124">New cmdlets</span></span>
- <span data-ttu-id="21fd1-125">PowerShellGet-förbättringarna omfattar att framtvinga signerade moduler och installera JEA-moduler</span><span class="sxs-lookup"><span data-stu-id="21fd1-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="21fd1-126">PackageManagement har lagt till stöd för containrar, CBS-installation, EXE-baserad installation, CAB-paket</span><span class="sxs-lookup"><span data-stu-id="21fd1-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="21fd1-127">Felsökningsförbättringar för DSC- och PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="21fd1-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="21fd1-128">Säkerhetsförbättringar, inklusive framtvingning av katalogsignerade moduler som kommer från Pull-servern och när du använder PowerShellGet-cmdletar</span><span class="sxs-lookup"><span data-stu-id="21fd1-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="21fd1-129">Svar på ett antal förfrågningar och problem från användare</span><span class="sxs-lookup"><span data-stu-id="21fd1-129">Responses to a number of user requests and issues</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21fd1-130">Innan du installerar WMF 5,1 på Windows Server 2008 eller Windows 7 kontrollerar du att WMF 3,0 inte är installerat.</span><span class="sxs-lookup"><span data-stu-id="21fd1-130">Before you install WMF 5.1 on Windows Server 2008 or Windows 7, confirm that WMF 3.0 isn't installed.</span></span> <span data-ttu-id="21fd1-131">Mer information finns i [WMF 5,1-krav för Windows Server 2008 R2 SP1 och Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span><span class="sxs-lookup"><span data-stu-id="21fd1-131">For more information, see [WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="21fd1-132">PowerShell-versioner</span><span class="sxs-lookup"><span data-stu-id="21fd1-132">PowerShell Editions</span></span>

<span data-ttu-id="21fd1-133">Från och med version 5,1 är PowerShell tillgängligt i olika versioner som kännetecknar varierande funktions uppsättningar och plattformens kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="21fd1-133">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="21fd1-134">**Desktop Edition:** Bygger på .NET Framework och ger kompatibilitet med skript och moduler som mål versioner av PowerShell som körs på fullständiga versioner av Windows, till exempel Server Core och Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="21fd1-134">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="21fd1-135">**Core-utgåva:** Bygger på .NET Core och ger kompatibilitet med skript och moduler som mål versioner av PowerShell som körs på begränsade versioner av Windows, till exempel Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="21fd1-135">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="21fd1-136">Lär dig mer om att använda PowerShell-versioner</span><span class="sxs-lookup"><span data-stu-id="21fd1-136">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="21fd1-137">Bestämma vilken version av PowerShell som körs med hjälp av $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="21fd1-137">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="21fd1-138">Filtrera get-module-resultat efter CompatiblePSEditions med parametern PSEdition</span><span class="sxs-lookup"><span data-stu-id="21fd1-138">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="21fd1-139">Förhindra skript körning om den inte körs på en kompatibel version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="21fd1-139">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/scripting/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="21fd1-140">Deklarera en moduls kompatibilitet för vissa PowerShell-versioner</span><span class="sxs-lookup"><span data-stu-id="21fd1-140">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="21fd1-141">Modul analys-cache</span><span class="sxs-lookup"><span data-stu-id="21fd1-141">Module Analysis Cache</span></span>

<span data-ttu-id="21fd1-142">Från och med WMF 5,1 ger PowerShell kontroll över filen som används för att cachelagra data om en modul, till exempel de kommandon som exporteras.</span><span class="sxs-lookup"><span data-stu-id="21fd1-142">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="21fd1-143">Som standard lagras cacheminnet i filen `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="21fd1-143">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="21fd1-144">Cachen läses normalt vid start vid sökning efter ett kommando och skrivs i en bakgrunds tråd någon gång efter att en modul har importer ATS.</span><span class="sxs-lookup"><span data-stu-id="21fd1-144">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="21fd1-145">Om du vill ändra standard platsen för cacheminnet anger du `$env:PSModuleAnalysisCachePath`-miljövariabeln innan du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21fd1-145">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="21fd1-146">Ändringar i denna miljö variabel påverkar bara underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="21fd1-146">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="21fd1-147">Värdet bör ge en fullständig sökväg (inklusive fil namnet) som PowerShell har behörighet att skapa och skriva filer.</span><span class="sxs-lookup"><span data-stu-id="21fd1-147">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="21fd1-148">Om du vill inaktivera filcachen ställer du in det här värdet på en ogiltig plats, till exempel:</span><span class="sxs-lookup"><span data-stu-id="21fd1-148">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="21fd1-149">Detta anger sökvägen till en ogiltig enhet.</span><span class="sxs-lookup"><span data-stu-id="21fd1-149">This sets the path to an invalid device.</span></span> <span data-ttu-id="21fd1-150">Om PowerShell inte kan skriva till sökvägen returneras inget fel, men du kan se fel rapportering med hjälp av en spårning:</span><span class="sxs-lookup"><span data-stu-id="21fd1-150">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="21fd1-151">När du skriver ut cacheminnet söker PowerShell efter moduler som inte längre finns för att undvika en onödigt stor cache.</span><span class="sxs-lookup"><span data-stu-id="21fd1-151">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="21fd1-152">Ibland är de här kontrollerna inte önskvärda, i så fall kan du inaktivera dem genom att ställa in:</span><span class="sxs-lookup"><span data-stu-id="21fd1-152">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="21fd1-153">Att ställa in den här miljövariabeln börjar gälla direkt i den aktuella processen.</span><span class="sxs-lookup"><span data-stu-id="21fd1-153">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="21fd1-154">Anger modul version</span><span class="sxs-lookup"><span data-stu-id="21fd1-154">Specifying module version</span></span>

<span data-ttu-id="21fd1-155">I WMF 5,1 fungerar `using module` på samma sätt som andra modulbaserade konstruktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21fd1-155">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="21fd1-156">Tidigare hade du inget sätt att ange en viss version av modulen. om det finns flera versioner, resulterade det i ett fel.</span><span class="sxs-lookup"><span data-stu-id="21fd1-156">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="21fd1-157">I WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="21fd1-157">In WMF 5.1:</span></span>

- <span data-ttu-id="21fd1-158">Du kan använda [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="21fd1-158">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

  <span data-ttu-id="21fd1-159">Den här hash-tabellen har samma format som `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="21fd1-159">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="21fd1-160">**Exempel:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="21fd1-160">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="21fd1-161">Om det finns flera versioner av modulen använder PowerShell **samma lösnings logik** som `Import-Module` och returnerar inte ett fel – samma beteende som `Import-Module` och `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="21fd1-161">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="21fd1-162">Förbättringar av pester</span><span class="sxs-lookup"><span data-stu-id="21fd1-162">Improvements to Pester</span></span>

<span data-ttu-id="21fd1-163">I WMF 5,1 har den version av pester som medföljer PowerShell uppdaterats från 3.3.5 till 3.4.0.</span><span class="sxs-lookup"><span data-stu-id="21fd1-163">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="21fd1-164">Den här uppdateringen ger bättre beteende för pester på Nano Server.</span><span class="sxs-lookup"><span data-stu-id="21fd1-164">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="21fd1-165">Du kan granska ändringar av skadegörare genom att inspektera [ändringsloggen](https://github.com/pester/Pester/blob/master/CHANGELOG.md) i GitHub-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="21fd1-165">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
