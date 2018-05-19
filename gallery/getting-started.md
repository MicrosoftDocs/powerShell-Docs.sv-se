---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Kom igång med PowerShell-galleriet
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="d242a-103">Kom igång med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="d242a-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="d242a-104">Hämtar objekt från PowerShell-galleriet till systemet kräver den [PowerShellGet](/powershell/module/powershellget) modul.</span><span class="sxs-lookup"><span data-stu-id="d242a-104">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="d242a-105">Modulen PowerShellGet hittar du i något av följande.</span><span class="sxs-lookup"><span data-stu-id="d242a-105">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="d242a-106">Du behöver inte logga in kan du hämta från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="d242a-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="d242a-107">Identifiering av objekt från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="d242a-107">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="d242a-108">Du hittar objekt i PowerShell-galleriet med hjälp av den **Sök** kontroll på den här webbplatsen, eller genom att gå igenom sidorna moduler och skript.</span><span class="sxs-lookup"><span data-stu-id="d242a-108">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="d242a-109">Du kan också hitta objekt från PowerShell-galleriet genom att köra den [hitta modulen][] och [hitta skriptet][] cmdlets, beroende på vilken objektet med `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="d242a-109">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="d242a-110">Filtrerar resultaten från galleriet kan göras med hjälp av följande parametrar:</span><span class="sxs-lookup"><span data-stu-id="d242a-110">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="d242a-111">Namn</span><span class="sxs-lookup"><span data-stu-id="d242a-111">Name</span></span>
- <span data-ttu-id="d242a-112">Allaversioner</span><span class="sxs-lookup"><span data-stu-id="d242a-112">AllVersions</span></span>
- <span data-ttu-id="d242a-113">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d242a-113">MinimumVersion</span></span>
- <span data-ttu-id="d242a-114">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d242a-114">RequiredVersion</span></span>
- <span data-ttu-id="d242a-115">Tagg</span><span class="sxs-lookup"><span data-stu-id="d242a-115">Tag</span></span>
- <span data-ttu-id="d242a-116">Innehåller</span><span class="sxs-lookup"><span data-stu-id="d242a-116">Includes</span></span>
- <span data-ttu-id="d242a-117">DscResource</span><span class="sxs-lookup"><span data-stu-id="d242a-117">DscResource</span></span>
- <span data-ttu-id="d242a-118">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d242a-118">RoleCapability</span></span>
- <span data-ttu-id="d242a-119">Kommando</span><span class="sxs-lookup"><span data-stu-id="d242a-119">Command</span></span>
- <span data-ttu-id="d242a-120">Filter</span><span class="sxs-lookup"><span data-stu-id="d242a-120">Filter</span></span>

<span data-ttu-id="d242a-121">Om du bara är intresserad av att identifiera specifika DSC-resurser i galleriet, kan du köra den [hitta DscResource] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d242a-121">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="d242a-122">Hitta DscResource returnerar data på DSC-resurser som ingår i galleriet.</span><span class="sxs-lookup"><span data-stu-id="d242a-122">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="d242a-123">Eftersom DSC resurser levereras alltid som en del av en modul, du fortfarande behöver köra [installera modulen][] att installera de DSC-resurserna.</span><span class="sxs-lookup"><span data-stu-id="d242a-123">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="d242a-124">Lär dig hur objekten i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="d242a-124">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="d242a-125">När du har hittat ett objekt som du är intresserad kan du vill veta mer om den.</span><span class="sxs-lookup"><span data-stu-id="d242a-125">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="d242a-126">Du kan göra detta genom att undersöka artikelns viss sida i galleriet.</span><span class="sxs-lookup"><span data-stu-id="d242a-126">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="d242a-127">På sidan, kommer du att kunna se alla metadata tillsammans med objektet.</span><span class="sxs-lookup"><span data-stu-id="d242a-127">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="d242a-128">Dessa metadata för en artikel tillhandahålls av objektets författare och verifieras inte av Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d242a-128">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="d242a-129">Ägaren av det kopplat starkt till Gallery-kontot som används för att publicera artikeln och är mer tillförlitlig än fältet Författare.</span><span class="sxs-lookup"><span data-stu-id="d242a-129">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="d242a-130">Om du upptäcker ett objekt som du inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för att objektet.</span><span class="sxs-lookup"><span data-stu-id="d242a-130">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="d242a-131">Om du kör [hitta modulen][] eller [hitta skriptet][], du kan visa informationen i det returnerade PSGetModuleInfo-objektet.</span><span class="sxs-lookup"><span data-stu-id="d242a-131">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="d242a-132">Till exempel köra `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returnerar data i modulen PSReadLine i galleriet.</span><span class="sxs-lookup"><span data-stu-id="d242a-132">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="d242a-133">Ladda ned objekt från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="d242a-133">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="d242a-134">Vi rekommenderar följande process när du hämtar objekt från PowerShell-galleriet:</span><span class="sxs-lookup"><span data-stu-id="d242a-134">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="d242a-135">Inspektera</span><span class="sxs-lookup"><span data-stu-id="d242a-135">Inspect</span></span>

<span data-ttu-id="d242a-136">Om du vill ladda ned ett objekt från galleriet för inspektion, kör du antingen den [spara modulen][] eller [spara skriptet][] cmdlet, beroende på vilken typ av objekt.</span><span class="sxs-lookup"><span data-stu-id="d242a-136">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="d242a-137">På så sätt kan du spara objektet lokalt utan att installera den och kontrollerar du innehållet för objektet.</span><span class="sxs-lookup"><span data-stu-id="d242a-137">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="d242a-138">Kom ihåg att ta bort det sparade objektet manuellt.</span><span class="sxs-lookup"><span data-stu-id="d242a-138">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="d242a-139">Vissa av dessa element skapats av Microsoft och andra skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="d242a-139">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="d242a-140">Microsoft rekommenderar att du läser innehåll och kod för artiklar i det här galleriet före installationen.</span><span class="sxs-lookup"><span data-stu-id="d242a-140">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="d242a-141">Om du upptäcker ett objekt som du inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för att objektet.</span><span class="sxs-lookup"><span data-stu-id="d242a-141">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="d242a-142">Installera</span><span class="sxs-lookup"><span data-stu-id="d242a-142">Install</span></span>

<span data-ttu-id="d242a-143">Installera ett objekt från galleriet för att köra antingen den [installera modulen][] eller [installationsskriptet][] cmdlet, beroende på vilken typ av objekt.</span><span class="sxs-lookup"><span data-stu-id="d242a-143">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="d242a-144">[installera modulen][] installerar modulen `$env:ProgramFiles\WindowsPowerShell\Modules` som standard.</span><span class="sxs-lookup"><span data-stu-id="d242a-144">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="d242a-145">Detta kräver att ett administratörskonto.</span><span class="sxs-lookup"><span data-stu-id="d242a-145">This requires an administrator account.</span></span> <span data-ttu-id="d242a-146">Om du lägger till den `-Scope CurrentUser` parametern modulen är installerad så att `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="d242a-146">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="d242a-147">[installationsskriptet][] installerar skriptet till `$env:ProgramFiles\WindowsPowerShell\Scripts` som standard.</span><span class="sxs-lookup"><span data-stu-id="d242a-147">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="d242a-148">Detta kräver att ett administratörskonto.</span><span class="sxs-lookup"><span data-stu-id="d242a-148">This requires an administrator account.</span></span> <span data-ttu-id="d242a-149">Om du lägger till den `-Scope CurrentUser` parametern skriptet installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="d242a-149">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="d242a-150">Som standard [installera modulen][] och [installationsskriptet][] installerar den senaste versionen av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="d242a-150">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="d242a-151">Installera en äldre version av objektet genom att lägga till den `-RequiredVersion` parameter.</span><span class="sxs-lookup"><span data-stu-id="d242a-151">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="d242a-152">Distribuera</span><span class="sxs-lookup"><span data-stu-id="d242a-152">Deploy</span></span>

<span data-ttu-id="d242a-153">Om du vill distribuera ett objekt från PowerShell-galleriet till Azure Automation klickar du på **till Azure Automation** på informationssidan för objektet.</span><span class="sxs-lookup"><span data-stu-id="d242a-153">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="d242a-154">Du omdirigeras till Azure-hanteringsportalen där du loggar in med dina Azure-autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="d242a-154">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="d242a-155">Observera att distribuera objekt med beroenden distribuerar alla beroenden till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="d242a-155">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="d242a-156">Knappen ”distribuera till Azure Automation-kan inaktiveras genom att lägga till den **AzureAutomationNotSupported** så att dina objektmetadata.</span><span class="sxs-lookup"><span data-stu-id="d242a-156">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="d242a-157">Läs mer om Azure Automation i den [Azure Automation](/azure/automation) dokumentation.</span><span class="sxs-lookup"><span data-stu-id="d242a-157">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="d242a-158">Uppdaterar objekt från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="d242a-158">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="d242a-159">Kör den [uppdatering modul] [] eller [Uppdateringsskriptet] [] cmdlet för att uppdatera objekt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="d242a-159">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="d242a-160">När du kör utan ytterligare parametrar [uppdatering modul] [] försöker uppdatera varje modul som har installerats genom att köra [installera modulen][].</span><span class="sxs-lookup"><span data-stu-id="d242a-160">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="d242a-161">Uppdatera selektivt moduler genom att lägga till den `-Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="d242a-161">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="d242a-162">På liknande sätt, när du kör utan ytterligare parametrar [Uppdateringsskriptet] [] också försöker uppdatera varje skript installerat genom att köra [installationsskriptet][].</span><span class="sxs-lookup"><span data-stu-id="d242a-162">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="d242a-163">Uppdatera selektivt skript genom att lägga till den `-Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="d242a-163">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="d242a-164">Lista över artiklar som du har installerat från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="d242a-164">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="d242a-165">Om du vill ta reda på vilka moduler som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledModule][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d242a-165">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="d242a-166">Det här kommandot visar alla moduler som du har i systemet som har installerats direkt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="d242a-166">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="d242a-167">På samma sätt för att ta reda på vilka skript som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledScript][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d242a-167">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="d242a-168">Det här kommandot listar alla skript som du har i systemet som har installerats direkt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="d242a-168">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[hitta DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[hitta modulen]: /powershell/module/powershellget/Find-Module
[Find-Module]: /powershell/module/powershellget/Find-Module
[hitta skriptet]: /powershell/module/powershellget/Find-Script
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[installera modulen]: /powershell/module/powershellget/Install-Module
[Install-Module]: /powershell/module/powershellget/Install-Module
[installationsskriptet]: /powershell/module/powershellget/Install-Script
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[spara modulen]: /powershell/module/powershellget/Save-Module
[Save-Module]: /powershell/module/powershellget/Save-Module
[spara skriptet]: /powershell/module/powershellget/Save-Script
[Save-Script]: /powershell/module/powershellget/Save-Script