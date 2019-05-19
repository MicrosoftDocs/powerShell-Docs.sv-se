---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: WMF 5.x viktig information
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856401"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="14c13-103">Windows Management Framework (WMF) 5.x viktig information</span><span class="sxs-lookup"><span data-stu-id="14c13-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="14c13-104">Ändringar av WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="14c13-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="14c13-105">PowerShell 5.0 lägger till en ny strukturerade **Information** stream</span><span class="sxs-lookup"><span data-stu-id="14c13-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="14c13-106">Förbättringar av DSC, inklusive fyra nya DSC-resurser:</span><span class="sxs-lookup"><span data-stu-id="14c13-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="14c13-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="14c13-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="14c13-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="14c13-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="14c13-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="14c13-109">ServiceSet</span></span>
  - <span data-ttu-id="14c13-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="14c13-110">ProcessSet</span></span>
- <span data-ttu-id="14c13-111">Har lagts till Just Enough Administration att aktivera rollbaserad administration via PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="14c13-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="14c13-112">PowerShell 5.0 utökar språk med användardefinierade klasser och uppräkningar</span><span class="sxs-lookup"><span data-stu-id="14c13-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="14c13-113">Förbättrade felsökningsfunktioner i PowerShell ISE och har lagts till fjärrfelsökning</span><span class="sxs-lookup"><span data-stu-id="14c13-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="14c13-114">Lagt till PowerShellGet och PackageManagement-moduler</span><span class="sxs-lookup"><span data-stu-id="14c13-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="14c13-115">Utökad loggning för PowerShell-skript och betyg</span><span class="sxs-lookup"><span data-stu-id="14c13-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="14c13-116">Lägga till syntaxen Cryptographic Message Syntax-cmdlets</span><span class="sxs-lookup"><span data-stu-id="14c13-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="14c13-117">WMF 5.0 innehåller NetworkSwitchManager-modulen för Windows</span><span class="sxs-lookup"><span data-stu-id="14c13-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="14c13-118">Lagt till modulen Microsoft.PowerShell.ODataUtils</span><span class="sxs-lookup"><span data-stu-id="14c13-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="14c13-119">Stöd har lagts till för Software Inventory Logging (SIL)</span><span class="sxs-lookup"><span data-stu-id="14c13-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="14c13-120">Ny server eller uppdatera cmdletar som svar på frågor och problem</span><span class="sxs-lookup"><span data-stu-id="14c13-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="14c13-121">WMF 5.1 ändras</span><span class="sxs-lookup"><span data-stu-id="14c13-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="14c13-122">WMF 5.1 innehåller PowerShell, WMI, WinRM och Software Inventory Logging (SIL) komponenterna som släpptes med Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="14c13-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="14c13-123">WMF 5.1 kan installeras på Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 och 2012 R2, och tillhandahåller flera förbättringar över WMF 5.0, inklusive:</span><span class="sxs-lookup"><span data-stu-id="14c13-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="14c13-124">Nya cmdletar</span><span class="sxs-lookup"><span data-stu-id="14c13-124">New cmdlets</span></span>
- <span data-ttu-id="14c13-125">PowerShellGet-förbättringarna omfattar att framtvinga signerade moduler och installera JEA-moduler</span><span class="sxs-lookup"><span data-stu-id="14c13-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="14c13-126">PackageManagement har lagt till stöd för containrar, CBS-installation, EXE-baserad installation, CAB-paket</span><span class="sxs-lookup"><span data-stu-id="14c13-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="14c13-127">Felsökningsförbättringar för DSC- och PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="14c13-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="14c13-128">Säkerhetsförbättringar, inklusive framtvingning av katalogsignerade moduler som kommer från Pull-servern och när du använder PowerShellGet-cmdletar</span><span class="sxs-lookup"><span data-stu-id="14c13-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="14c13-129">Svar på ett antal förfrågningar och problem från användare</span><span class="sxs-lookup"><span data-stu-id="14c13-129">Responses to a number of user requests and issues</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="14c13-130">PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="14c13-130">PowerShell Editions</span></span>

<span data-ttu-id="14c13-131">Från och med version 5.1 finns finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="14c13-131">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="14c13-132">**Desktop Edition:** Bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows-skrivbordet.</span><span class="sxs-lookup"><span data-stu-id="14c13-132">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="14c13-133">**Core Edition:** Bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="14c13-133">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="14c13-134">Läs mer om hur du använder PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="14c13-134">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="14c13-135">Fastställa utgåva av PowerShell med hjälp av $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="14c13-135">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="14c13-136">Filtrera resultatet för Get-Module av CompatiblePSEditions med hjälp av parametern PSEdition</span><span class="sxs-lookup"><span data-stu-id="14c13-136">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="14c13-137">Förhindra körning av skript, såvida inte köras på en kompatibel version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="14c13-137">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="14c13-138">Deklarera en modul kompatibilitet med specifika versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="14c13-138">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="14c13-139">Module Analysis Cache</span><span class="sxs-lookup"><span data-stu-id="14c13-139">Module Analysis Cache</span></span>

<span data-ttu-id="14c13-140">Från och med WMF 5.1 finns ger PowerShell kontroll över den fil som används för att cachelagra data om en modul, till exempel kommandon som du exporterar.</span><span class="sxs-lookup"><span data-stu-id="14c13-140">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="14c13-141">Det här cacheminnet lagras som standard i filen `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="14c13-141">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="14c13-142">Cachen läses vanligtvis vid start vid sökning efter ett kommando och skrivs i en bakgrundstråd någon gång när en modul har importerats.</span><span class="sxs-lookup"><span data-stu-id="14c13-142">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="14c13-143">Du kan ändra standardplatsen för cachen, ange den `$env:PSModuleAnalysisCachePath` miljövariabeln innan du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14c13-143">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="14c13-144">Ändringar i den här miljövariabeln påverkar endast underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="14c13-144">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="14c13-145">Värdet ska namnge en fullständig sökväg (inklusive filnamnet) som PowerShell har behörighet att skapa och skriva filer.</span><span class="sxs-lookup"><span data-stu-id="14c13-145">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="14c13-146">Om du vill inaktivera filcachen det här värdet till en ogiltig plats, till exempel:</span><span class="sxs-lookup"><span data-stu-id="14c13-146">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="14c13-147">Detta anger sökvägen till en ogiltig enhet.</span><span class="sxs-lookup"><span data-stu-id="14c13-147">This sets the path to an invalid device.</span></span> <span data-ttu-id="14c13-148">Om PowerShell inte kan skrivas till sökvägen, inget fel returneras, men du kan se Felrapportering med hjälp av en spårning:</span><span class="sxs-lookup"><span data-stu-id="14c13-148">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="14c13-149">När du skriver ut cacheminnet, kontrollerar PowerShell för moduler som inte längre finns för att undvika ett onödigt stort cache.</span><span class="sxs-lookup"><span data-stu-id="14c13-149">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="14c13-150">Ibland är kontrollerna inte önskvärt, då du kan inaktivera dem genom att ange:</span><span class="sxs-lookup"><span data-stu-id="14c13-150">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="14c13-151">Ange den här miljövariabeln börjar gälla omedelbart i den aktuella processen.</span><span class="sxs-lookup"><span data-stu-id="14c13-151">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="14c13-152">Ange Modulversion</span><span class="sxs-lookup"><span data-stu-id="14c13-152">Specifying module version</span></span>

<span data-ttu-id="14c13-153">I WMF 5.1 `using module` fungerar på samma sätt som andra modul-relaterade konstruktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14c13-153">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="14c13-154">Tidigare fick du inte vill ange en viss modul-version. Om det finns flera versioner finns, resulterade detta i ett fel.</span><span class="sxs-lookup"><span data-stu-id="14c13-154">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="14c13-155">I WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="14c13-155">In WMF 5.1:</span></span>

- <span data-ttu-id="14c13-156">Du kan använda [ModuleSpecification-konstruktor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="14c13-156">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
  <span data-ttu-id="14c13-157">Den här hashtabellen har samma format som `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="14c13-157">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="14c13-158">**Exempel:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="14c13-158">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="14c13-159">Om det finns flera versioner av modulen, PowerShell använder den **samma lösning logik** som `Import-Module` och inte returneras ett fel – på samma sätt som när `Import-Module` och `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="14c13-159">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="14c13-160">Förbättringar av lära</span><span class="sxs-lookup"><span data-stu-id="14c13-160">Improvements to Pester</span></span>

<span data-ttu-id="14c13-161">Versionen av Pester som levereras med PowerShell har blivit uppdaterad från 3.3.5 i WMF 5.1 till 3.4.0.</span><span class="sxs-lookup"><span data-stu-id="14c13-161">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="14c13-162">Den här uppdateringen kan bättre beteende för Pester på Nano Server.</span><span class="sxs-lookup"><span data-stu-id="14c13-162">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="14c13-163">Du kan granska ändringarna i beskrivet genom att granska den [ändringsloggen](https://github.com/pester/Pester/blob/master/CHANGELOG.md) i GitHub-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="14c13-163">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
