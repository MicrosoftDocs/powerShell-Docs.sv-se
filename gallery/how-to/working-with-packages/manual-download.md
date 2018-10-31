---
ms.date: 09/11/2018
contributor: JKeithB
keywords: galleriet, powershell, psgallery
title: Manuell paketnedladdning
ms.openlocfilehash: 0952aa4ec474850af5219fb2e0e9ee3e954b0f9a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004144"
---
# <a name="manual-package-download"></a><span data-ttu-id="516e1-103">Manuell paketnedladdning</span><span class="sxs-lookup"><span data-stu-id="516e1-103">Manual Package Download</span></span>

<span data-ttu-id="516e1-104">Powershell-galleriet har stöd för ett paket laddades ned från webbplatsen direkt, utan att använda PowerShellGet-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="516e1-104">The Powershell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="516e1-105">Paketet laddas ned som ett NuGet-paketet (.nupkg)-fil som kan sedan enkelt kopieras till en intern lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="516e1-105">The package will be downloaded as a NuGet package (.nupkg) file, which can then be easily copied to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="516e1-106">Ladda ned manuell paket är **inte** avsedd som en ersättning för cmdleten Install-Module.</span><span class="sxs-lookup"><span data-stu-id="516e1-106">Manual package download is **not** intended as a replacement for the Install-Module cmdlet.</span></span>
> <span data-ttu-id="516e1-107">Ladda ned paketet installerar inte modulen eller skript.</span><span class="sxs-lookup"><span data-stu-id="516e1-107">Downloading the package does not install the module or script.</span></span> <span data-ttu-id="516e1-108">Beroenden ingår inte i NuGet-paketet som hämtas.</span><span class="sxs-lookup"><span data-stu-id="516e1-108">Dependencies are not included in the NuGet package downloaded.</span></span> <span data-ttu-id="516e1-109">Följande instruktioner tillhandahålls endast för referens.</span><span class="sxs-lookup"><span data-stu-id="516e1-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="516e1-110">Använda manuell hämtning för att hämta ett paket</span><span class="sxs-lookup"><span data-stu-id="516e1-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="516e1-111">Varje sida innehåller en länk för manuell hämtning, som visas här:</span><span class="sxs-lookup"><span data-stu-id="516e1-111">Each page has a link for Manual Download, as shown here:</span></span>

![Manuell hämtning](../../Images/packagedisplaypagewithpseditions.png)

<span data-ttu-id="516e1-113">Om du vill hämta manuellt klickar du på **Filnedladdning raw nupkg**.</span><span class="sxs-lookup"><span data-stu-id="516e1-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="516e1-114">En kopia av paketet kopieras till mappen för din webbläsare med namnet `<name>.<version>.nupkg`.</span><span class="sxs-lookup"><span data-stu-id="516e1-114">A copy of the package copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="516e1-115">Ett NuGet-paket är ett ZIP-arkiv med extra filer som innehåller information om innehållet i paketet.</span><span class="sxs-lookup"><span data-stu-id="516e1-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="516e1-116">Vissa webbläsare, till exempel Internet Explorer automatiskt ersätta den `.nupkg` filnamnstillägget med `.zip`.</span><span class="sxs-lookup"><span data-stu-id="516e1-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="516e1-117">För att expandera paketet, byta namn på den `.nupkg` filen till `.zip`vid behov, sedan extrahera innehållet till en lokal mapp.</span><span class="sxs-lookup"><span data-stu-id="516e1-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="516e1-118">En fil för NuGet-paketet innehåller följande NuGet-specifika element som inte ingår i den ursprungliga paketerade koden:</span><span class="sxs-lookup"><span data-stu-id="516e1-118">A NuGet package file includes the following NuGet-specific elements that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="516e1-119">En mapp med namnet `_rels` – innehåller en `.rels` -fil som innehåller beroenden</span><span class="sxs-lookup"><span data-stu-id="516e1-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="516e1-120">En mapp med namnet `package` -innehåller NuGet-specifika data</span><span class="sxs-lookup"><span data-stu-id="516e1-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="516e1-121">En fil med namnet `[Content_Types].xml` – beskriver hur filtillägg som PowerShellGet fungerar med NuGet</span><span class="sxs-lookup"><span data-stu-id="516e1-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="516e1-122">En fil med namnet `<name>.nuspec` -innehåller stora mängd metadata</span><span class="sxs-lookup"><span data-stu-id="516e1-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="516e1-123">Installera PowerShell-moduler från ett NuGet-paket</span><span class="sxs-lookup"><span data-stu-id="516e1-123">Installing PowerShell Modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="516e1-124">De här anvisningarna **inte** ger samma resultat som att köra `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="516e1-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="516e1-125">De här anvisningarna uppfyller minimikraven.</span><span class="sxs-lookup"><span data-stu-id="516e1-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="516e1-126">De är inte avsedda att ersätta `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="516e1-126">They are not intended to be a replacement for `Install-Module`.</span></span> <span data-ttu-id="516e1-127">Vissa steg som utförs av `Install-Module` ingår inte.</span><span class="sxs-lookup"><span data-stu-id="516e1-127">Some steps performed by `Install-Module` are not included.</span></span>

<span data-ttu-id="516e1-128">Den enklaste metoden är att ta bort NuGet-specifika elementen från mappen.</span><span class="sxs-lookup"><span data-stu-id="516e1-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="516e1-129">Det innebär att PowerShell-kod som skapats av paketets upphovsman.</span><span class="sxs-lookup"><span data-stu-id="516e1-129">This leaves the PowerShell code created by the package author.</span></span> <span data-ttu-id="516e1-130">Stegen är:</span><span class="sxs-lookup"><span data-stu-id="516e1-130">The steps are:</span></span>

1. <span data-ttu-id="516e1-131">Extrahera innehållet i NuGet-paketet till en lokal mapp.</span><span class="sxs-lookup"><span data-stu-id="516e1-131">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="516e1-132">Ta bort NuGet-specifika elementen från mappen.</span><span class="sxs-lookup"><span data-stu-id="516e1-132">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="516e1-133">Byt namn på mappen.</span><span class="sxs-lookup"><span data-stu-id="516e1-133">Rename the folder.</span></span> <span data-ttu-id="516e1-134">Standardnamnet på mappen är vanligtvis `<name>.<version>`.</span><span class="sxs-lookup"><span data-stu-id="516e1-134">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="516e1-135">Versionen kan innehålla ”-förhandsversion” om modulen har märkts som en förhandsversion.</span><span class="sxs-lookup"><span data-stu-id="516e1-135">The version can include "-prerelease" if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="516e1-136">Byt namn på mappen till bara modulens namn.</span><span class="sxs-lookup"><span data-stu-id="516e1-136">Rename the folder to just the module name.</span></span> <span data-ttu-id="516e1-137">Till exempel ”azurerm.storage.5.0.4 förhandsversion” till ”azurerm.storage”.</span><span class="sxs-lookup"><span data-stu-id="516e1-137">For example, "azurerm.storage.5.0.4-preview" becomes "azurerm.storage".</span></span>
4. <span data-ttu-id="516e1-138">Kopiera mappen till din PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="516e1-138">Copy the folder to your PSModulePath.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="516e1-139">Manuell hämtning inkluderar inte eventuella beroenden som krävs av modulen.</span><span class="sxs-lookup"><span data-stu-id="516e1-139">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="516e1-140">Om paketet har beroenden, måste de installeras i systemet så att den här modulen ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="516e1-140">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="516e1-141">PowerShell-galleriet visar alla beroenden som krävs av paketet.</span><span class="sxs-lookup"><span data-stu-id="516e1-141">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="516e1-142">Installera PowerShell-skript från ett NuGet-paket</span><span class="sxs-lookup"><span data-stu-id="516e1-142">Installing PowerShell Scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="516e1-143">De här anvisningarna **inte** ger samma resultat som att köra `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="516e1-143">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="516e1-144">De här anvisningarna uppfyller minimikraven.</span><span class="sxs-lookup"><span data-stu-id="516e1-144">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="516e1-145">De är inte avsedda att ersätta `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="516e1-145">They are not intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="516e1-146">Den enklaste metoden är att extrahera NuGet-paketet, därefter använder du skriptet direkt.</span><span class="sxs-lookup"><span data-stu-id="516e1-146">The easiest approach is to extract the NuGet package, then use the script directly.</span></span> <span data-ttu-id="516e1-147">Stegen är:</span><span class="sxs-lookup"><span data-stu-id="516e1-147">The steps are:</span></span>

1. <span data-ttu-id="516e1-148">Extrahera innehållet i NuGet-paketet.</span><span class="sxs-lookup"><span data-stu-id="516e1-148">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="516e1-149">Den `.PS1` filen i mappen kan användas direkt från den här platsen.</span><span class="sxs-lookup"><span data-stu-id="516e1-149">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="516e1-150">Du kan ta bort NuGet-specifika elementen i mappen.</span><span class="sxs-lookup"><span data-stu-id="516e1-150">You may delete the NuGet-specific elements in the folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="516e1-151">Manuell hämtning inkluderar inte eventuella beroenden som krävs av modulen.</span><span class="sxs-lookup"><span data-stu-id="516e1-151">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="516e1-152">Om paketet har beroenden, måste de installeras i systemet så att den här modulen ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="516e1-152">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="516e1-153">PowerShell-galleriet visar alla beroenden som krävs av paketet.</span><span class="sxs-lookup"><span data-stu-id="516e1-153">The PowerShell Gallery shows all dependencies required by the package.</span></span>
