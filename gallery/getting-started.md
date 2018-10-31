---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Kom igång med PowerShell-galleriet
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225683"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="407c2-103">Komma igång med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="407c2-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="407c2-104">Det korrekta sättet att installera paket från PowerShell-galleriet är att använda cmdletarna i den [PowerShellGet](/powershell/module/powershellget) modulen.</span><span class="sxs-lookup"><span data-stu-id="407c2-104">The proper way to install packages from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="407c2-105">Du behöver inte logga in att ladda ned objekt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="407c2-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="407c2-106">Det är möjligt att ladda ned ett paket från PowerShell-galleriet direkt, men detta är inte en rekommenderad metod.</span><span class="sxs-lookup"><span data-stu-id="407c2-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="407c2-107">Mer information finns i [manuell paketet hämta](/powershell/gallery/how-to/working-with-packages/manual-download).</span><span class="sxs-lookup"><span data-stu-id="407c2-107">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="407c2-108">Identifiering av paket från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="407c2-108">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="407c2-109">Du kan hitta paket i PowerShell-galleriet med hjälp av den **Search** kontroll på den här webbplatsen, eller genom att bläddra igenom sidorna moduler och skript.</span><span class="sxs-lookup"><span data-stu-id="407c2-109">You can find packages in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="407c2-110">Du kan också hitta paket från PowerShell-galleriet genom att köra den [Find-Module][] och [Find-Script][] cmdlet: ar, beroende på vilken objekt med `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="407c2-110">You can also find packages from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="407c2-111">Filtrerar resultaten från galleriet kan du göra detta med hjälp av följande parametrar:</span><span class="sxs-lookup"><span data-stu-id="407c2-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="407c2-112">Namn</span><span class="sxs-lookup"><span data-stu-id="407c2-112">Name</span></span>
- <span data-ttu-id="407c2-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="407c2-113">AllVersions</span></span>
- <span data-ttu-id="407c2-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="407c2-114">MinimumVersion</span></span>
- <span data-ttu-id="407c2-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="407c2-115">RequiredVersion</span></span>
- <span data-ttu-id="407c2-116">Tagg</span><span class="sxs-lookup"><span data-stu-id="407c2-116">Tag</span></span>
- <span data-ttu-id="407c2-117">Innehåller</span><span class="sxs-lookup"><span data-stu-id="407c2-117">Includes</span></span>
- <span data-ttu-id="407c2-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="407c2-118">DscResource</span></span>
- <span data-ttu-id="407c2-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="407c2-119">RoleCapability</span></span>
- <span data-ttu-id="407c2-120">Kommando</span><span class="sxs-lookup"><span data-stu-id="407c2-120">Command</span></span>
- <span data-ttu-id="407c2-121">Filter</span><span class="sxs-lookup"><span data-stu-id="407c2-121">Filter</span></span>

<span data-ttu-id="407c2-122">Om du bara vill identifiera specifika DSC-resurser i galleriet, du kan köra den [Sök-DscResource] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="407c2-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="407c2-123">Sök-DscResource returnerar data på DSC-resurser som ingår i galleriet.</span><span class="sxs-lookup"><span data-stu-id="407c2-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="407c2-124">Eftersom DSC-resurser levereras alltid som en del av en modul, du fortfarande behöver köra [Install-Module][] att installera dessa DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="407c2-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="407c2-125">Lära dig mer om paketen i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="407c2-125">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="407c2-126">När du har identifierat ett paket som du är intresserad av kan du lära dig mer om den.</span><span class="sxs-lookup"><span data-stu-id="407c2-126">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="407c2-127">Du kan göra detta genom att undersöka det paketet specifik sida i galleriet.</span><span class="sxs-lookup"><span data-stu-id="407c2-127">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="407c2-128">På sidan, kommer du att kunna se alla metadata som har överförts med paketet.</span><span class="sxs-lookup"><span data-stu-id="407c2-128">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="407c2-129">Dessa metadata kommer från paketets författare och verifieras inte av Microsoft.</span><span class="sxs-lookup"><span data-stu-id="407c2-129">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="407c2-130">Ägaren av paketet är alltså tätt kopplade till kontot galleriet som används för att publicera paketet och är mer tillförlitlig än fältet Författare.</span><span class="sxs-lookup"><span data-stu-id="407c2-130">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="407c2-131">Om du upptäcker ett paket som du anser inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för det paketet.</span><span class="sxs-lookup"><span data-stu-id="407c2-131">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="407c2-132">Om du kör [Find-Module][] eller [Find-Script][], du kan visa dessa data i det returnerade PSGetModuleInfo-objektet.</span><span class="sxs-lookup"><span data-stu-id="407c2-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="407c2-133">Till exempel köra `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="407c2-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="407c2-134">Returnerar data i modulen PSReadLine i galleriet.</span><span class="sxs-lookup"><span data-stu-id="407c2-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="407c2-135">Ladda ned paket från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="407c2-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="407c2-136">Vi rekommenderar följande process när du laddar ned paket från PowerShell-galleriet:</span><span class="sxs-lookup"><span data-stu-id="407c2-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="407c2-137">Granska</span><span class="sxs-lookup"><span data-stu-id="407c2-137">Inspect</span></span>

<span data-ttu-id="407c2-138">Om du vill ladda ned ett paket från galleriet för granskning, kör du antingen den [Save-Module][] eller [Save-Script][] cmdlet, beroende på typen av paketet.</span><span class="sxs-lookup"><span data-stu-id="407c2-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="407c2-139">På så sätt kan du spara paketet lokalt utan att installera den och granska paketinnehållet.</span><span class="sxs-lookup"><span data-stu-id="407c2-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="407c2-140">Kom ihåg att ta bort det sparade paketet manuellt.</span><span class="sxs-lookup"><span data-stu-id="407c2-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="407c2-141">Vissa av dessa paket skapats av Microsoft och andra skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="407c2-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="407c2-142">Microsoft rekommenderar att du läser igenom innehållet och koden för paket på det här galleriet före installationen.</span><span class="sxs-lookup"><span data-stu-id="407c2-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="407c2-143">Om du upptäcker ett paket som du anser inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för det paketet.</span><span class="sxs-lookup"><span data-stu-id="407c2-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="407c2-144">Installera</span><span class="sxs-lookup"><span data-stu-id="407c2-144">Install</span></span>

<span data-ttu-id="407c2-145">Om du vill installera ett paket från galleriet för användning, kör du antingen den [Install-Module][] eller [Install-Script][] cmdlet, beroende på typen av paketet.</span><span class="sxs-lookup"><span data-stu-id="407c2-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="407c2-146">[Install-Module][] installerar modulen till `$env:ProgramFiles\WindowsPowerShell\Modules` som standard.</span><span class="sxs-lookup"><span data-stu-id="407c2-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="407c2-147">Detta kräver ett administratörskonto.</span><span class="sxs-lookup"><span data-stu-id="407c2-147">This requires an administrator account.</span></span> <span data-ttu-id="407c2-148">Om du lägger till den `-Scope CurrentUser` parametern modulen installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="407c2-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="407c2-149">[Install-Script][] installerar skriptet till `$env:ProgramFiles\WindowsPowerShell\Scripts` som standard.</span><span class="sxs-lookup"><span data-stu-id="407c2-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="407c2-150">Detta kräver ett administratörskonto.</span><span class="sxs-lookup"><span data-stu-id="407c2-150">This requires an administrator account.</span></span> <span data-ttu-id="407c2-151">Om du lägger till den `-Scope CurrentUser` parametern skriptet installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="407c2-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="407c2-152">Som standard [Install-Module][] och [Install-Script][] installerar den senaste versionen av ett paket.</span><span class="sxs-lookup"><span data-stu-id="407c2-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="407c2-153">Installera en äldre version av paketet lägger till den `-RequiredVersion` parametern.</span><span class="sxs-lookup"><span data-stu-id="407c2-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="407c2-154">Distribuera</span><span class="sxs-lookup"><span data-stu-id="407c2-154">Deploy</span></span>

<span data-ttu-id="407c2-155">Om du vill distribuera ett paket från PowerShell-galleriet i Azure Automation, klickar du på **distribuera till Azure Automation** på sidan med paketet.</span><span class="sxs-lookup"><span data-stu-id="407c2-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="407c2-156">Du omdirigeras till Azure-hanteringsportalen där du loggar in med dina autentiseringsuppgifter för Azure-konto.</span><span class="sxs-lookup"><span data-stu-id="407c2-156">You will be redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="407c2-157">Observera att distribuera paket med beroenden distribuerar alla beroenden till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="407c2-157">Note that deploying packages with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="407c2-158">Knappen ”distribuera till Azure Automation-kan inaktiveras genom att lägga till den **AzureAutomationNotSupported** tagg till din paketmetadata.</span><span class="sxs-lookup"><span data-stu-id="407c2-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="407c2-159">Läs mer om Azure Automation i den [Azure Automation](/azure/automation) dokumentation.</span><span class="sxs-lookup"><span data-stu-id="407c2-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="407c2-160">Uppdaterar paket från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="407c2-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="407c2-161">Om du vill uppdatera paket som installeras från PowerShell-galleriet, kör du antingen [Update-Module] [-] eller [Uppdateringsskriptet] [] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="407c2-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="407c2-162">När du kör utan ytterligare parametrar, [Update-Module] [] försöker uppdatera varje modul som har installerats genom att köra [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="407c2-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="407c2-163">För att selektivt uppdatera moduler, lägger du till den `-Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="407c2-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="407c2-164">På samma sätt när kör utan ytterligare parametrar, [Uppdateringsskriptet] [-] också försöker uppdatera varje skript som har installerats genom att köra [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="407c2-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="407c2-165">För att selektivt uppdatera skript, lägger du till den `-Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="407c2-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="407c2-166">Lista över paket som du har installerat från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="407c2-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="407c2-167">Om du vill ta reda på vilka moduler som du har installerat från PowerShell-galleriet kan du köra den [Get-InstalledModule][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="407c2-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="407c2-168">Det här kommandot visar alla moduler som du har på datorn som har installerats direkt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="407c2-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="407c2-169">På samma sätt för att ta reda på vilka skript som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledScript][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="407c2-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="407c2-170">Det här kommandot visar alla skript som du har på datorn som har installerats direkt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="407c2-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Sök-DscResource]: /powershell/module/powershellget/Find-DscResource
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
