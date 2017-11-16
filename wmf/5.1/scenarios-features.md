---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
title: Nya scenarier och funktioner i WMF 5.1
ms.openlocfilehash: 430781c5c9a59fc544db4f94098313ae1e9cf610
ms.sourcegitcommit: a6ee6e64d369ecf82c730411bed9750278fdb5c1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/18/2017
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="fb886-103">Nya scenarier och funktioner i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="fb886-103">New Scenarios and Features in WMF 5.1</span></span> #

> <span data-ttu-id="fb886-104">Obs: Den här informationen är preliminär och kan ändras.</span><span class="sxs-lookup"><span data-stu-id="fb886-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="fb886-105">PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="fb886-105">PowerShell Editions</span></span> ##
<span data-ttu-id="fb886-106">Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="fb886-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="fb886-107">**Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="fb886-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="fb886-108">**Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="fb886-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="fb886-109">**Lär dig mer om hur du använder PowerShell-versioner**</span><span class="sxs-lookup"><span data-stu-id="fb886-109">**Learn more about using PowerShell Editions**</span></span>
- [<span data-ttu-id="fb886-110">Fastställa körs version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb886-110">Determine running edition of PowerShell</span></span>]()
- [<span data-ttu-id="fb886-111">Deklarera en modul kompatibilitet med vissa versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb886-111">Declare a module's compatibility to specific PowerShell versions</span></span>]()
- [<span data-ttu-id="fb886-112">Filtrera Get-Module resultat av CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="fb886-112">Filter Get-Module results by CompatiblePSEditions</span></span>]()
- [<span data-ttu-id="fb886-113">Förhindra körning av skript om du inte på en kompatibel version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb886-113">Prevent script execution unless run on a compatible edition of PowerShell</span></span>]()

## <a name="catalog-cmdlets"></a><span data-ttu-id="fb886-114">Katalog-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="fb886-114">Catalog Cmdlets</span></span>  

<span data-ttu-id="fb886-115">Två nya cmdletar har lagts till i den [Microsoft.PowerShell.Security](https://technet.microsoft.com/en-us/library/hh847877.aspx) modulen; dessa generera och verifiera filer för Windows-katalogen.</span><span class="sxs-lookup"><span data-stu-id="fb886-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](https://technet.microsoft.com/en-us/library/hh847877.aspx) module; these generate and validate Windows catalog files.</span></span>  

###<a name="new-filecatalog"></a><span data-ttu-id="fb886-116">Ny FileCatalog</span><span class="sxs-lookup"><span data-stu-id="fb886-116">New-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="fb886-117">Ny FileCatalog skapar en Windows-katalogfil för mappar och filer.</span><span class="sxs-lookup"><span data-stu-id="fb886-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span> <span data-ttu-id="fb886-118">Den här katalogfilen innehåller hashvärden för alla filer i angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="fb886-118">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="fb886-119">Användarna kan distribuera mapparna tillsammans med motsvarande katalogfil som representerar mapparna.</span><span class="sxs-lookup"><span data-stu-id="fb886-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="fb886-120">Den här informationen är användbar för att kontrollera om några ändringar har gjorts till mapparna sedan tiden för skapandet av katalogen.</span><span class="sxs-lookup"><span data-stu-id="fb886-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="fb886-121">Katalogen version 1 och 2 stöds.</span><span class="sxs-lookup"><span data-stu-id="fb886-121">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="fb886-122">Version 1 används SHA1-hash-algoritm för att skapa filhash; version 2 används SHA256.</span><span class="sxs-lookup"><span data-stu-id="fb886-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="fb886-123">Katalogversion 2 stöds inte på *Windows Server 2008 R2* eller *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="fb886-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span> <span data-ttu-id="fb886-124">Du bör använda katalogversion 2 på *Windows 8*, *Windows Server 2012*, och senare operativsystem.</span><span class="sxs-lookup"><span data-stu-id="fb886-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>  

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="fb886-125">Då skapas katalogfilen.</span><span class="sxs-lookup"><span data-stu-id="fb886-125">This creates the catalog file.</span></span> 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

<span data-ttu-id="fb886-126">Att kontrollera integriteten för katalogfil (Pester.cat i ovanstående exempel), signera den med hjälp av [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb886-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>   


###<a name="test-filecatalog"></a><span data-ttu-id="fb886-127">Testa FileCatalog</span><span class="sxs-lookup"><span data-stu-id="fb886-127">Test-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="fb886-128">Testa FileCatalog verifierar katalogen som representerar en uppsättning mappar.</span><span class="sxs-lookup"><span data-stu-id="fb886-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span> 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="fb886-129">Denna cmdlet Jämför filer hashvärdena och deras relativa sökvägar finns i *katalog* med de som på *disk*.</span><span class="sxs-lookup"><span data-stu-id="fb886-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span> <span data-ttu-id="fb886-130">Om den identifierar eventuella matchningsfel mellan värden och sökvägar returnerar status som *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="fb886-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span> <span data-ttu-id="fb886-131">Användare kan hämta den här informationen med hjälp av den *-detaljerad* parameter.</span><span class="sxs-lookup"><span data-stu-id="fb886-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="fb886-132">Visar även signering status för katalogen i *signatur* -egenskap som motsvarar anropar [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet på katalogfilen.</span><span class="sxs-lookup"><span data-stu-id="fb886-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span> <span data-ttu-id="fb886-133">Användare kan också hoppa över en fil vid verifiering av med hjälp av den *- FilesToSkip* parameter.</span><span class="sxs-lookup"><span data-stu-id="fb886-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span> 


## <a name="module-analysis-cache"></a><span data-ttu-id="fb886-134">Modulen analys Cache</span><span class="sxs-lookup"><span data-stu-id="fb886-134">Module Analysis Cache</span></span> ##
<span data-ttu-id="fb886-135">Från och med WMF 5.1 ger PowerShell kontroll över den fil som används för att cachelagra data om en modul, till exempel kommandon som exporteras.</span><span class="sxs-lookup"><span data-stu-id="fb886-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="fb886-136">Det här cacheminnet lagras som standard i filen `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="fb886-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="fb886-137">Cachen läses vanligtvis vid start vid sökning efter ett kommando och sparas på en bakgrundstråd senare när en modul har importerats.</span><span class="sxs-lookup"><span data-stu-id="fb886-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="fb886-138">Du kan ändra standardplatsen för cachen, ange den `$env:PSModuleAnalysisCachePath` miljövariabeln innan du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb886-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="fb886-139">Ändringar i den här miljövariabeln påverkar endast underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="fb886-139">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="fb886-140">Värdet ska namnge den fullständiga sökvägen (inklusive filnamnet) som har behörighet att skapa och skriva filer för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb886-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="fb886-141">Om du vill inaktivera filcachen det här värdet till en ogiltig plats, till exempel:</span><span class="sxs-lookup"><span data-stu-id="fb886-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="fb886-142">Anger sökvägen till en ogiltig enhet.</span><span class="sxs-lookup"><span data-stu-id="fb886-142">This sets the path to an invalid device.</span></span> <span data-ttu-id="fb886-143">Om PowerShell går inte att skriva till sökvägen inget fel returneras, men du kan se Felrapportering med hjälp av en spårning:</span><span class="sxs-lookup"><span data-stu-id="fb886-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="fb886-144">När du skriver ut cacheminnet, kontrollerar PowerShell för moduler som inte längre finns för att undvika ett onödigt stor cache.</span><span class="sxs-lookup"><span data-stu-id="fb886-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="fb886-145">Ibland är kontrollerna inte önskvärt, då du kan inaktivera dem genom att ange:</span><span class="sxs-lookup"><span data-stu-id="fb886-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="fb886-146">Ange den här miljövariabeln börjar gälla omedelbart i den aktuella processen.</span><span class="sxs-lookup"><span data-stu-id="fb886-146">Setting this environment variable will take effect immediately in the current process.</span></span>

##<a name="specifying-module-version"></a><span data-ttu-id="fb886-147">Ange Modulversion</span><span class="sxs-lookup"><span data-stu-id="fb886-147">Specifying module version</span></span>

<span data-ttu-id="fb886-148">I WMF 5.1 `using module` fungerar på samma sätt som andra relaterade modulen konstruktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb886-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="fb886-149">Tidigare fick du inte vill ange en viss modul-version. Om det fanns flera versioner finns, resulterade detta i ett fel.</span><span class="sxs-lookup"><span data-stu-id="fb886-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>


<span data-ttu-id="fb886-150">I WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="fb886-150">In WMF 5.1:</span></span>

* <span data-ttu-id="fb886-151">Du kan använda [ModuleSpecification konstruktor (hash-tabell)](https://msdn.microsoft.com/library/jj136290).</span><span class="sxs-lookup"><span data-stu-id="fb886-151">You can use [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span></span> <span data-ttu-id="fb886-152">Den här hashtabellen har samma format som `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="fb886-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="fb886-153">**Exempel:**`using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="fb886-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="fb886-154">Om det finns flera versioner av modulen, PowerShell använder den **samma upplösning logik** som `Import-Module` och returnerar inte ett fel--samma beteende som `Import-Module` och `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="fb886-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>


##<a name="improvements-to-pester"></a><span data-ttu-id="fb886-155">Förbättringar av lära</span><span class="sxs-lookup"><span data-stu-id="fb886-155">Improvements to Pester</span></span>
<span data-ttu-id="fb886-156">I WMF 5.1 har version av Pester som levereras med PowerShell uppdaterats från 3.3.5 till 3.4.0 med tillägget för genomförande https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e som möjliggör bättre beteende för Lära på Nano Server.</span><span class="sxs-lookup"><span data-stu-id="fb886-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span> 

<span data-ttu-id="fb886-157">Du kan granska ändringar i versioner 3.3.5 3.4.0 genom att inspektera ChangeLog.md filen på: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="fb886-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>

