---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Kom igång med PowerShell-galleriet
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: 1082b13115c5c5be4b76574ba55307b3e567983f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52576897"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="3da99-103">Komma igång med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="3da99-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="3da99-104">PowerShell-galleriet är en paketdatabas som innehåller skript, moduler och du kan hämta och använda DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="3da99-104">The PowerShell Gallery is a package repository containing scripts, modules, and DSC resources you can download and leverage.</span></span> <span data-ttu-id="3da99-105">Du använder cmdlets i den [PowerShellGet](/powershell/module/powershellget) modul för att installera paket från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="3da99-105">You use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module to install packages from the PowerShell Gallery.</span></span> <span data-ttu-id="3da99-106">Du behöver inte logga in att ladda ned objekt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="3da99-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="3da99-107">Det är möjligt att ladda ned ett paket från PowerShell-galleriet direkt, men detta är inte en rekommenderad metod.</span><span class="sxs-lookup"><span data-stu-id="3da99-107">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="3da99-108">Mer information finns i [manuell paketet hämta](/powershell/gallery/how-to/working-with-packages/manual-download).</span><span class="sxs-lookup"><span data-stu-id="3da99-108">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="3da99-109">Identifiering av paket från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="3da99-109">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="3da99-110">Du kan hitta paket i PowerShell-galleriet med hjälp av den **Search** kontrollen i PowerShell-galleriet [startsida](https://www.powershellgallery.com), eller genom att gå igenom de moduler och skript från den [paket sidan ](https://www.powershellgallery.com/packages).</span><span class="sxs-lookup"><span data-stu-id="3da99-110">You can find packages in the PowerShell Gallery by using the **Search** control on the PowerShell Gallery's [home page](https://www.powershellgallery.com), or by browsing through the Modules and Scripts from the [Packages page](https://www.powershellgallery.com/packages).</span></span> <span data-ttu-id="3da99-111">Du kan också hitta paket från PowerShell-galleriet genom att köra den [Find-Module][], [Find-DscResource], och [Find-Script][] cmdlet: ar, beroende på typen package med `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="3da99-111">You can also find packages from the PowerShell Gallery by running the [Find-Module][], [Find-DscResource], and [Find-Script][] cmdlets, depending on the package type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="3da99-112">Du kan filtrera resultaten från galleriet med hjälp av följande parametrar:</span><span class="sxs-lookup"><span data-stu-id="3da99-112">You can filter results from the Gallery by using the following parameters:</span></span>

- <span data-ttu-id="3da99-113">Namn</span><span class="sxs-lookup"><span data-stu-id="3da99-113">Name</span></span>
- <span data-ttu-id="3da99-114">AllVersions</span><span class="sxs-lookup"><span data-stu-id="3da99-114">AllVersions</span></span>
- <span data-ttu-id="3da99-115">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3da99-115">MinimumVersion</span></span>
- <span data-ttu-id="3da99-116">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3da99-116">RequiredVersion</span></span>
- <span data-ttu-id="3da99-117">Tagg</span><span class="sxs-lookup"><span data-stu-id="3da99-117">Tag</span></span>
- <span data-ttu-id="3da99-118">Innehåller</span><span class="sxs-lookup"><span data-stu-id="3da99-118">Includes</span></span>
- <span data-ttu-id="3da99-119">DscResource</span><span class="sxs-lookup"><span data-stu-id="3da99-119">DscResource</span></span>
- <span data-ttu-id="3da99-120">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="3da99-120">RoleCapability</span></span>
- <span data-ttu-id="3da99-121">Kommando</span><span class="sxs-lookup"><span data-stu-id="3da99-121">Command</span></span>
- <span data-ttu-id="3da99-122">Filter</span><span class="sxs-lookup"><span data-stu-id="3da99-122">Filter</span></span>

<span data-ttu-id="3da99-123">Om du bara vill identifiera specifika DSC-resurser i galleriet, du kan köra den [Find-DscResource] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3da99-123">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="3da99-124">Sök-DscResource returnerar data på DSC-resurser som ingår i galleriet.</span><span class="sxs-lookup"><span data-stu-id="3da99-124">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="3da99-125">Eftersom DSC-resurser levereras alltid som en del av en modul, du fortfarande behöver köra [Install-Module][] att installera dessa DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="3da99-125">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="3da99-126">Lära dig mer om paketen i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="3da99-126">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="3da99-127">När du har identifierat ett paket som du är intresserad av kan du lära dig mer om den.</span><span class="sxs-lookup"><span data-stu-id="3da99-127">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="3da99-128">Du kan göra detta genom att undersöka det paketet specifik sida i galleriet.</span><span class="sxs-lookup"><span data-stu-id="3da99-128">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="3da99-129">På sidan, kommer du att kunna se alla metadata som har överförts med paketet.</span><span class="sxs-lookup"><span data-stu-id="3da99-129">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="3da99-130">Dessa metadata kommer från paketets författare och verifieras inte av Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3da99-130">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="3da99-131">Ägaren av paketet är alltså tätt kopplade till kontot galleriet som används för att publicera paketet och är mer tillförlitlig än fältet Författare.</span><span class="sxs-lookup"><span data-stu-id="3da99-131">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="3da99-132">Om du upptäcker ett paket som du anser inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för det paketet.</span><span class="sxs-lookup"><span data-stu-id="3da99-132">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="3da99-133">Om du kör [Find-Module][] eller [Find-Script][], du kan visa dessa data i det returnerade PSGetModuleInfo-objektet.</span><span class="sxs-lookup"><span data-stu-id="3da99-133">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="3da99-134">Till exempel köra `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="3da99-134">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="3da99-135">Returnerar data i modulen PSReadLine i galleriet.</span><span class="sxs-lookup"><span data-stu-id="3da99-135">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="3da99-136">Ladda ned paket från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="3da99-136">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="3da99-137">Vi rekommenderar följande process när du laddar ned paket från PowerShell-galleriet:</span><span class="sxs-lookup"><span data-stu-id="3da99-137">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="3da99-138">Granska</span><span class="sxs-lookup"><span data-stu-id="3da99-138">Inspect</span></span>

<span data-ttu-id="3da99-139">Om du vill ladda ned ett paket från galleriet för granskning, kör du antingen den [Save-Module][] eller [Save-Script][] cmdlet, beroende på typen av paketet.</span><span class="sxs-lookup"><span data-stu-id="3da99-139">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="3da99-140">På så sätt kan du spara paketet lokalt utan att installera den och granska paketinnehållet.</span><span class="sxs-lookup"><span data-stu-id="3da99-140">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="3da99-141">Kom ihåg att ta bort det sparade paketet manuellt.</span><span class="sxs-lookup"><span data-stu-id="3da99-141">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="3da99-142">Vissa av dessa paket skapats av Microsoft och andra skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="3da99-142">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="3da99-143">Microsoft rekommenderar att du läser igenom innehållet och koden för paket på det här galleriet före installationen.</span><span class="sxs-lookup"><span data-stu-id="3da99-143">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="3da99-144">Om du upptäcker ett paket som du anser inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för det paketet.</span><span class="sxs-lookup"><span data-stu-id="3da99-144">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="3da99-145">Installera</span><span class="sxs-lookup"><span data-stu-id="3da99-145">Install</span></span>

<span data-ttu-id="3da99-146">Om du vill installera ett paket från galleriet för användning, kör du antingen den [Install-Module][] eller [Install-Script][] cmdlet, beroende på typen av paketet.</span><span class="sxs-lookup"><span data-stu-id="3da99-146">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="3da99-147">[Install-Module][] installerar modulen till `$env:ProgramFiles\WindowsPowerShell\Modules` som standard.</span><span class="sxs-lookup"><span data-stu-id="3da99-147">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="3da99-148">Detta kräver ett administratörskonto.</span><span class="sxs-lookup"><span data-stu-id="3da99-148">This requires an administrator account.</span></span> <span data-ttu-id="3da99-149">Om du lägger till den `-Scope CurrentUser` parametern modulen installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="3da99-149">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="3da99-150">[Install-Script][] installerar skriptet till `$env:ProgramFiles\WindowsPowerShell\Scripts` som standard.</span><span class="sxs-lookup"><span data-stu-id="3da99-150">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="3da99-151">Detta kräver ett administratörskonto.</span><span class="sxs-lookup"><span data-stu-id="3da99-151">This requires an administrator account.</span></span> <span data-ttu-id="3da99-152">Om du lägger till den `-Scope CurrentUser` parametern skriptet installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="3da99-152">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="3da99-153">Som standard [Install-Module][] och [Install-Script][] installerar den senaste versionen av ett paket.</span><span class="sxs-lookup"><span data-stu-id="3da99-153">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="3da99-154">Installera en äldre version av paketet lägger till den `-RequiredVersion` parametern.</span><span class="sxs-lookup"><span data-stu-id="3da99-154">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="3da99-155">Distribuera</span><span class="sxs-lookup"><span data-stu-id="3da99-155">Deploy</span></span>

<span data-ttu-id="3da99-156">Om du vill distribuera ett paket från PowerShell-galleriet i Azure Automation, klickar du på **Azure Automation**, klicka sedan på **distribuera till Azure Automation** på sidan med paketet.</span><span class="sxs-lookup"><span data-stu-id="3da99-156">To deploy a package from the PowerShell Gallery to Azure Automation, click **Azure Automation**, then click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="3da99-157">Du omdirigeras till Azure-hanteringsportalen där du loggar in med dina autentiseringsuppgifter för Azure-konto.</span><span class="sxs-lookup"><span data-stu-id="3da99-157">You are redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="3da99-158">Observera att distribuera paket med beroenden distribuerar alla beroenden till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="3da99-158">Note that deploying packages with dependencies deploys all the dependencies to Azure Automation.</span></span> <span data-ttu-id="3da99-159">Knappen ”distribuera till Azure Automation-kan inaktiveras genom att lägga till den **AzureAutomationNotSupported** tagg till din paketmetadata.</span><span class="sxs-lookup"><span data-stu-id="3da99-159">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="3da99-160">Läs mer om Azure Automation i den [Azure Automation](/azure/automation) dokumentation.</span><span class="sxs-lookup"><span data-stu-id="3da99-160">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="3da99-161">Uppdaterar paket från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="3da99-161">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="3da99-162">Om du vill uppdatera paket som installeras från PowerShell-galleriet, kör du antingen [Update-Module] [-] eller [Uppdateringsskriptet] [] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3da99-162">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="3da99-163">När du kör utan ytterligare parametrar, [Update-Module] [] försöker uppdatera alla moduler som har installerats genom att köra [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="3da99-163">When run without any additional parameters, [Update-Module][] attempts to update all modules installed by running [Install-Module][].</span></span> <span data-ttu-id="3da99-164">För att selektivt uppdatera moduler, lägger du till den `-Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="3da99-164">To selectively update modules, add the `-Name` parameter.</span></span> 

<span data-ttu-id="3da99-165">På samma sätt när kör utan ytterligare parametrar, [Uppdateringsskriptet] [-] också försöker uppdatera alla skript som har installerats genom att köra [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="3da99-165">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update all scripts installed by running [Install-Script][].</span></span> <span data-ttu-id="3da99-166">För att selektivt uppdatera skript, lägger du till den `-Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="3da99-166">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="3da99-167">Lista över paket som du har installerat från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="3da99-167">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="3da99-168">Om du vill ta reda på vilka moduler som du har installerat från PowerShell-galleriet kan du köra den [Get-InstalledModule][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3da99-168">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="3da99-169">Det här kommandot visar alla moduler som du har på datorn som har installerats direkt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="3da99-169">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="3da99-170">På samma sätt för att ta reda på vilka skript som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledScript][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3da99-170">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="3da99-171">Det här kommandot visar alla skript som du har på datorn som har installerats direkt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="3da99-171">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
