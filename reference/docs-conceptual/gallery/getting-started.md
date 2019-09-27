---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Kom igång med PowerShell-galleriet
ms.openlocfilehash: ee3fe7d9c65ad1a8f9ffd2ddec0f4ce6659bc3d5
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329164"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="b9e30-103">Komma igång med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="b9e30-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="b9e30-104">PowerShell-galleriet är en paket lagrings plats som innehåller skript, moduler och DSC-resurser som du kan hämta och utnyttja.</span><span class="sxs-lookup"><span data-stu-id="b9e30-104">The PowerShell Gallery is a package repository containing scripts, modules, and DSC resources you can download and leverage.</span></span> <span data-ttu-id="b9e30-105">Du kan använda cmdletarna i [PowerShellGet](/powershell/module/powershellget) -modulen för att installera paket från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-105">You use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module to install packages from the PowerShell Gallery.</span></span> <span data-ttu-id="b9e30-106">Du behöver inte logga in för att ladda ned objekt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="b9e30-107">Det går att ladda ned ett paket från PowerShell-galleriet direkt, men detta är inte en rekommenderad metod.</span><span class="sxs-lookup"><span data-stu-id="b9e30-107">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span> <span data-ttu-id="b9e30-108">Mer information finns i [manuell paket hämtning](how-to/working-with-packages/manual-download.md).</span><span class="sxs-lookup"><span data-stu-id="b9e30-108">For more details, see [Manual Package Download](how-to/working-with-packages/manual-download.md).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="b9e30-109">Identifiera paket från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="b9e30-109">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="b9e30-110">Du kan hitta paket i PowerShell-galleriet med hjälp av **Sök** kontrollen på [start sidan](https://www.powershellgallery.com)för PowerShell-galleriet eller genom att bläddra bland modulerna och skripten på [sidan paket](https://www.powershellgallery.com/packages).</span><span class="sxs-lookup"><span data-stu-id="b9e30-110">You can find packages in the PowerShell Gallery by using the **Search** control on the PowerShell Gallery's [home page](https://www.powershellgallery.com), or by browsing through the Modules and Scripts from the [Packages page](https://www.powershellgallery.com/packages).</span></span> <span data-ttu-id="b9e30-111">Du kan också hitta paket från PowerShell-galleriet genom att köra cmdletarna [Sök-modul][], [find-dscresource Keyword Supports]och [Sök – skript][] , beroende på paket typen, med `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="b9e30-111">You can also find packages from the PowerShell Gallery by running the [Find-Module][], [Find-DscResource], and [Find-Script][] cmdlets, depending on the package type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="b9e30-112">Du kan filtrera resultat från galleriet med hjälp av följande parametrar:</span><span class="sxs-lookup"><span data-stu-id="b9e30-112">You can filter results from the Gallery by using the following parameters:</span></span>

- <span data-ttu-id="b9e30-113">Name</span><span class="sxs-lookup"><span data-stu-id="b9e30-113">Name</span></span>
- <span data-ttu-id="b9e30-114">AllVersions</span><span class="sxs-lookup"><span data-stu-id="b9e30-114">AllVersions</span></span>
- <span data-ttu-id="b9e30-115">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b9e30-115">MinimumVersion</span></span>
- <span data-ttu-id="b9e30-116">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b9e30-116">RequiredVersion</span></span>
- <span data-ttu-id="b9e30-117">Tagga</span><span class="sxs-lookup"><span data-stu-id="b9e30-117">Tag</span></span>
- <span data-ttu-id="b9e30-118">Inkluderar</span><span class="sxs-lookup"><span data-stu-id="b9e30-118">Includes</span></span>
- <span data-ttu-id="b9e30-119">Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="b9e30-119">DscResource</span></span>
- <span data-ttu-id="b9e30-120">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="b9e30-120">RoleCapability</span></span>
- <span data-ttu-id="b9e30-121">Kommando</span><span class="sxs-lookup"><span data-stu-id="b9e30-121">Command</span></span>
- <span data-ttu-id="b9e30-122">Filter</span><span class="sxs-lookup"><span data-stu-id="b9e30-122">Filter</span></span>

<span data-ttu-id="b9e30-123">Om du bara är intresse rad av att identifiera vissa DSC-resurser i galleriet kan du köra cmdleten [find-dscresource Keyword Supports][] .</span><span class="sxs-lookup"><span data-stu-id="b9e30-123">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource][] cmdlet.</span></span> <span data-ttu-id="b9e30-124">Find-Dscresource Keyword Supports returnerar data på DSC-resurser som finns i galleriet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-124">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span> <span data-ttu-id="b9e30-125">Eftersom DSC-resurser alltid levereras som en del av en modul, behöver du fortfarande köra [Installera-modul][] för att installera dessa DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="b9e30-125">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="b9e30-126">Lär dig om paket i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="b9e30-126">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="b9e30-127">När du har identifierat ett paket som du är intresse rad av kanske du vill veta mer om det.</span><span class="sxs-lookup"><span data-stu-id="b9e30-127">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="b9e30-128">Det kan du göra genom att undersöka Paketets aktuella sida i galleriet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-128">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="b9e30-129">På den sidan kan du se alla metadata som har laddats upp med paketet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-129">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="b9e30-130">Dessa metadata tillhandahålls av paketets författare och verifieras inte av Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b9e30-130">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="b9e30-131">Paketets ägare är starkt bunden till Galleri kontot som används för att publicera paketet och är mer tillförlitligt än fältet författare.</span><span class="sxs-lookup"><span data-stu-id="b9e30-131">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="b9e30-132">Om du upptäcker ett paket som du tycker att du inte har publicerat i en godkänd tro klickar du på **rapportera missbruk** på paketets sida.</span><span class="sxs-lookup"><span data-stu-id="b9e30-132">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="b9e30-133">Om du kör [Sök-modul][] eller [Sök – skript][]kan du visa dessa data i det returnerade PSGetModuleInfo-objektet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-133">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="b9e30-134">Att köra `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returnerar till exempel data i PSReadLine-modulen i galleriet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-134">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="b9e30-135">Hämta paket från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="b9e30-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="b9e30-136">Vi uppmuntrar följande process när du laddar ned paket från PowerShell-galleriet:</span><span class="sxs-lookup"><span data-stu-id="b9e30-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="b9e30-137">allmänt</span><span class="sxs-lookup"><span data-stu-id="b9e30-137">Inspect</span></span>

<span data-ttu-id="b9e30-138">Om du vill ladda ned ett paket från galleriet för granskning kör du antingen cmdleten [Spara-modul][] eller [Spara – skript][] , beroende på paket typen.</span><span class="sxs-lookup"><span data-stu-id="b9e30-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="b9e30-139">På så sätt kan du spara paketet lokalt utan att installera det och granska paket innehållet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="b9e30-140">Kom ihåg att ta bort det sparade paketet manuellt.</span><span class="sxs-lookup"><span data-stu-id="b9e30-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="b9e30-141">Några av de här paketen har skapats av Microsoft och andra har skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="b9e30-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span> <span data-ttu-id="b9e30-142">Microsoft rekommenderar att du granskar innehållet och koden i paketen i det här galleriet före installationen.</span><span class="sxs-lookup"><span data-stu-id="b9e30-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="b9e30-143">Om du upptäcker ett paket som du tycker att du inte har publicerat i en godkänd tro klickar du på **rapportera missbruk** på paketets sida.</span><span class="sxs-lookup"><span data-stu-id="b9e30-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="b9e30-144">Installera</span><span class="sxs-lookup"><span data-stu-id="b9e30-144">Install</span></span>

<span data-ttu-id="b9e30-145">Om du vill installera ett paket från galleriet för användning kör du antingen cmdleten [Installera-modul][] eller [Installera – skript][] , beroende på typ av paket.</span><span class="sxs-lookup"><span data-stu-id="b9e30-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="b9e30-146">[Installera-modul][] installerar modulen `$env:ProgramFiles\WindowsPowerShell\Modules` som standard.</span><span class="sxs-lookup"><span data-stu-id="b9e30-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="b9e30-147">Detta kräver ett administratörs konto.</span><span class="sxs-lookup"><span data-stu-id="b9e30-147">This requires an administrator account.</span></span> <span data-ttu-id="b9e30-148">Om du lägger till `-Scope CurrentUser` parametern installeras modulen till. `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="b9e30-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="b9e30-149">[Installera – skript][] installerar skriptet till `$env:ProgramFiles\WindowsPowerShell\Scripts` som standard.</span><span class="sxs-lookup"><span data-stu-id="b9e30-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="b9e30-150">Detta kräver ett administratörs konto.</span><span class="sxs-lookup"><span data-stu-id="b9e30-150">This requires an administrator account.</span></span> <span data-ttu-id="b9e30-151">Om du lägger till `-Scope CurrentUser` parametern installeras skriptet till. `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`</span><span class="sxs-lookup"><span data-stu-id="b9e30-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="b9e30-152">Som standard installerar [Installera-modul][] och [Installera – skript][] den senaste versionen av ett paket.</span><span class="sxs-lookup"><span data-stu-id="b9e30-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span> <span data-ttu-id="b9e30-153">Lägg till `-RequiredVersion` parametern om du vill installera en äldre version av paketet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="b9e30-154">Distribuera</span><span class="sxs-lookup"><span data-stu-id="b9e30-154">Deploy</span></span>

<span data-ttu-id="b9e30-155">Om du vill distribuera ett paket från PowerShell-galleriet till Azure Automation klickar du på **Azure Automation**och klickar sedan på **distribuera till Azure Automation** på paket informations sidan.</span><span class="sxs-lookup"><span data-stu-id="b9e30-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Azure Automation**, then click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="b9e30-156">Du omdirigeras till Azure-Hanteringsportal där du loggar in med dina autentiseringsuppgifter för Azure-kontot.</span><span class="sxs-lookup"><span data-stu-id="b9e30-156">You are redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="b9e30-157">Observera att distribution av paket med beroenden distribuerar alla beroenden till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="b9e30-157">Note that deploying packages with dependencies deploys all the dependencies to Azure Automation.</span></span> <span data-ttu-id="b9e30-158">Knappen distribuera till Azure Automation kan inaktive ras genom att **AzureAutomationNotSupported** -taggen läggs till i paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="b9e30-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="b9e30-159">Mer information om Azure Automation finns i [Azure Automation](/azure/automation) -dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="b9e30-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="b9e30-160">Uppdaterar paket från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="b9e30-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="b9e30-161">Om du vill uppdatera paket som är installerade från PowerShell-galleriet kör du antingen cmdleten [Update-module] [] eller [Update-Script] [].</span><span class="sxs-lookup"><span data-stu-id="b9e30-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="b9e30-162">När körs utan ytterligare parametrar försöker [Update-module] [] uppdatera alla moduler som installerats genom att köra [Installera-modul][].</span><span class="sxs-lookup"><span data-stu-id="b9e30-162">When run without any additional parameters, [Update-Module][] attempts to update all modules installed by running [Install-Module][].</span></span> <span data-ttu-id="b9e30-163">Om du vill uppdatera moduler selektivt `-Name` lägger du till parametern.</span><span class="sxs-lookup"><span data-stu-id="b9e30-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="b9e30-164">På samma sätt försöker [Update-Script] [] också uppdatera alla skript som installeras genom att köra [Installera – skript][]när de körs utan ytterligare parametrar.</span><span class="sxs-lookup"><span data-stu-id="b9e30-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update all scripts installed by running [Install-Script][].</span></span> <span data-ttu-id="b9e30-165">Om du vill uppdatera skript selektivt `-Name` lägger du till parametern.</span><span class="sxs-lookup"><span data-stu-id="b9e30-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="b9e30-166">List paket som du har installerat från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="b9e30-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="b9e30-167">Om du vill ta reda på vilka moduler som du har installerat från PowerShell-galleriet kör du cmdleten [Get-InstalledModule][] .</span><span class="sxs-lookup"><span data-stu-id="b9e30-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="b9e30-168">Detta kommando visar alla moduler som finns på ditt system som har installerats direkt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="b9e30-169">Om du vill ta reda på vilka skript som du har installerat från PowerShell-galleriet kör du cmdleten [Get-InstalledScript][] .</span><span class="sxs-lookup"><span data-stu-id="b9e30-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="b9e30-170">Det här kommandot visar alla skript som finns på ditt system som installerades direkt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b9e30-170">This command lists all the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-Dscresource Keyword Supports]: /powershell/module/powershellget/Find-DscResource
[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Sök-modul]: /powershell/module/powershellget/Find-Module
[Find-Module]: /powershell/module/powershellget/Find-Module
[Sök – skript]: /powershell/module/powershellget/Find-Script
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Installera-modul]: /powershell/module/powershellget/Install-Module
[Install-Module]: /powershell/module/powershellget/Install-Module
[Installera – skript]: /powershell/module/powershellget/Install-Script
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Spara-modul]: /powershell/module/powershellget/Save-Module
[Save-Module]: /powershell/module/powershellget/Save-Module
[Spara – skript]: /powershell/module/powershellget/Save-Script
[Save-Script]: /powershell/module/powershellget/Save-Script
