---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galleri, PowerShell, psgallery
title: Manuell paketnedladdning
ms.openlocfilehash: e562f5b94b4d2caa7d31269a324e417d1a9e844a
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278736"
---
# <a name="manual-package-download"></a><span data-ttu-id="eb1df-103">Manuell paketnedladdning</span><span class="sxs-lookup"><span data-stu-id="eb1df-103">Manual Package Download</span></span>

<span data-ttu-id="eb1df-104">PowerShell-galleriet har stöd för att ladda ned ett paket från webbplatsen direkt, utan att använda PowerShellGet-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="eb1df-104">The PowerShell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="eb1df-105">Du kan ladda ned alla paket som en`.nupkg`-fil (NuGet Package) som du sedan kan kopiera till en intern lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="eb1df-105">You can download any package as a NuGet package (`.nupkg`) file, which you can then copy to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="eb1df-106">Manuell nedladdning av paketet är **inte** tänkt att ersätta `Install-Module`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eb1df-106">Manual package download is **not** intended as a replacement for the `Install-Module` cmdlet.</span></span>
> <span data-ttu-id="eb1df-107">Om du hämtar paketet installeras inte modulen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="eb1df-107">Downloading the package doesn't install the module or script.</span></span> <span data-ttu-id="eb1df-108">Beroenden ingår inte i NuGet-paketet som hämtats.</span><span class="sxs-lookup"><span data-stu-id="eb1df-108">Dependencies aren't included in the NuGet package downloaded.</span></span> <span data-ttu-id="eb1df-109">Följande instruktioner anges endast i referens syfte.</span><span class="sxs-lookup"><span data-stu-id="eb1df-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="eb1df-110">Använda manuell nedladdning för att hämta ett paket</span><span class="sxs-lookup"><span data-stu-id="eb1df-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="eb1df-111">Varje sida har en länk för manuell hämtning, som du ser här:</span><span class="sxs-lookup"><span data-stu-id="eb1df-111">Each page has a link for Manual Download, as shown here:</span></span>

![Manuell nedladdning](media/manual-download/packagedisplaypagewithpseditions.png)

<span data-ttu-id="eb1df-113">Om du vill ladda ned manuellt klickar **du på Hämta RAW nupkg-filen**.</span><span class="sxs-lookup"><span data-stu-id="eb1df-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="eb1df-114">En kopia av paketet kopieras till download-mappen för din webbläsare med namnet `<name>.<version>.nupkg`.</span><span class="sxs-lookup"><span data-stu-id="eb1df-114">A copy of the package is copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="eb1df-115">Ett NuGet-paket är ett ZIP-arkiv med extra filer som innehåller information om paketets innehåll.</span><span class="sxs-lookup"><span data-stu-id="eb1df-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="eb1df-116">Vissa webbläsare, som Internet Explorer, ersätter automatiskt `.nupkg` fil namns tillägget med `.zip`.</span><span class="sxs-lookup"><span data-stu-id="eb1df-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="eb1df-117">Om du vill expandera paketet byter du namn på `.nupkg`-filen till `.zip`, om det behövs, och extraherar sedan innehållet till en lokal mapp.</span><span class="sxs-lookup"><span data-stu-id="eb1df-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="eb1df-118">En NuGet-paketfil innehåller följande **NuGet element** som inte ingår i den ursprungliga paketerade koden:</span><span class="sxs-lookup"><span data-stu-id="eb1df-118">A NuGet package file includes the following **NuGet-specific elements** that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="eb1df-119">En mapp med namnet `_rels`-innehåller en `.rels`-fil som visar beroenden</span><span class="sxs-lookup"><span data-stu-id="eb1df-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="eb1df-120">En mapp med namnet `package` – innehåller NuGet data</span><span class="sxs-lookup"><span data-stu-id="eb1df-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="eb1df-121">En fil med namnet `[Content_Types].xml` – beskriver hur tillägg som PowerShellGet fungerar med NuGet</span><span class="sxs-lookup"><span data-stu-id="eb1df-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="eb1df-122">En fil med namnet `<name>.nuspec` – innehåller en samling metadata</span><span class="sxs-lookup"><span data-stu-id="eb1df-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="eb1df-123">Installera PowerShell-moduler från ett NuGet-paket</span><span class="sxs-lookup"><span data-stu-id="eb1df-123">Installing PowerShell modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="eb1df-124">Dessa instruktioner ger **inte** samma resultat som att köra `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="eb1df-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="eb1df-125">De här anvisningarna uppfyller minimi kraven.</span><span class="sxs-lookup"><span data-stu-id="eb1df-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="eb1df-126">De är inte avsedda att ersätta `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="eb1df-126">They aren't intended to be a replacement for `Install-Module`.</span></span>
> <span data-ttu-id="eb1df-127">Vissa steg som utförs av `Install-Module` ingår inte.</span><span class="sxs-lookup"><span data-stu-id="eb1df-127">Some steps performed by `Install-Module` aren't included.</span></span>

<span data-ttu-id="eb1df-128">Det enklaste sättet är att ta bort de NuGet elementen från mappen.</span><span class="sxs-lookup"><span data-stu-id="eb1df-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="eb1df-129">Att ta bort elementen lämnar PowerShell-koden som skapats av paketets författare.</span><span class="sxs-lookup"><span data-stu-id="eb1df-129">Removing the elements leaves the PowerShell code created by the package author.</span></span>
<span data-ttu-id="eb1df-130">En lista över NuGet element finns i [använda manuell hämtning för att hämta ett paket](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="eb1df-130">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

<span data-ttu-id="eb1df-131">Stegen är följande:</span><span class="sxs-lookup"><span data-stu-id="eb1df-131">The steps are as follows:</span></span>

1. <span data-ttu-id="eb1df-132">Avblockera NuGet-filen`.nupkg`(Internet-Hämtad-paket), till exempel med hjälp av `Unblock-File -Path C:\Downloads\module.nupkg`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb1df-132">Unblock the Internet-downloaded NuGet package (`.nupkg`) file, for example using `Unblock-File -Path C:\Downloads\module.nupkg` cmdlet.</span></span>
2. <span data-ttu-id="eb1df-133">Extrahera innehållet i NuGet-paketet till en lokal mapp.</span><span class="sxs-lookup"><span data-stu-id="eb1df-133">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="eb1df-134">Ta bort de NuGet elementen från mappen.</span><span class="sxs-lookup"><span data-stu-id="eb1df-134">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="eb1df-135">Byt namn på mappen.</span><span class="sxs-lookup"><span data-stu-id="eb1df-135">Rename the folder.</span></span> <span data-ttu-id="eb1df-136">Standard namnet på mappen `<name>.<version>`vanligt vis.</span><span class="sxs-lookup"><span data-stu-id="eb1df-136">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="eb1df-137">Versionen kan innehålla `-prerelease` om modulen är Taggad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="eb1df-137">The version can include `-prerelease` if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="eb1df-138">Byt namn på mappen till bara modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="eb1df-138">Rename the folder to just the module name.</span></span> <span data-ttu-id="eb1df-139">`azurerm.storage.5.0.4-preview` blir till exempel `azurerm.storage`.</span><span class="sxs-lookup"><span data-stu-id="eb1df-139">For example, `azurerm.storage.5.0.4-preview` becomes `azurerm.storage`.</span></span>
4. <span data-ttu-id="eb1df-140">Kopiera mappen till en av mapparna i `$env:PSModulePath value`.</span><span class="sxs-lookup"><span data-stu-id="eb1df-140">Copy the folder to one of the folders in the `$env:PSModulePath value`.</span></span> <span data-ttu-id="eb1df-141">`$env:PSModulePath` är en semikolonavgränsad uppsättning sökvägar där PowerShell ska söka efter moduler.</span><span class="sxs-lookup"><span data-stu-id="eb1df-141">`$env:PSModulePath` is a semicolon-delimited set of paths in which PowerShell should look for modules.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb1df-142">Den manuella hämtningen innehåller inte några beroenden som krävs av modulen.</span><span class="sxs-lookup"><span data-stu-id="eb1df-142">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="eb1df-143">Om paketet har beroenden måste de installeras i systemet för att modulen ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="eb1df-143">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="eb1df-144">PowerShell-galleriet visar alla beroenden som krävs av paketet.</span><span class="sxs-lookup"><span data-stu-id="eb1df-144">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="eb1df-145">Installera PowerShell-skript från ett NuGet-paket</span><span class="sxs-lookup"><span data-stu-id="eb1df-145">Installing PowerShell scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="eb1df-146">Dessa instruktioner ger **inte** samma resultat som att köra `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="eb1df-146">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="eb1df-147">De här anvisningarna uppfyller minimi kraven.</span><span class="sxs-lookup"><span data-stu-id="eb1df-147">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="eb1df-148">De är inte avsedda att ersätta `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="eb1df-148">They aren't intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="eb1df-149">Den enklaste metoden är att extrahera NuGet-paketet och sedan använda skriptet direkt.</span><span class="sxs-lookup"><span data-stu-id="eb1df-149">The easiest approach is to extract the NuGet package, then use the script directly.</span></span>

<span data-ttu-id="eb1df-150">Stegen är följande:</span><span class="sxs-lookup"><span data-stu-id="eb1df-150">The steps are as follows:</span></span>

1. <span data-ttu-id="eb1df-151">Avblockera NuGet-filen`.nupkg`(Internet-Hämtad-paket), till exempel med hjälp av `Unblock-File -Path C:\Downloads\package.nupkg`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb1df-151">Unblock the Internet-downloaded NuGet package (`.nupkg`) file, for example using `Unblock-File -Path C:\Downloads\package.nupkg` cmdlet.</span></span>
2. <span data-ttu-id="eb1df-152">Extrahera innehållet i NuGet-paketet.</span><span class="sxs-lookup"><span data-stu-id="eb1df-152">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="eb1df-153">`.PS1` filen i mappen kan användas direkt från den här platsen.</span><span class="sxs-lookup"><span data-stu-id="eb1df-153">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="eb1df-154">Du kan ta bort de NuGet elementen i mappen.</span><span class="sxs-lookup"><span data-stu-id="eb1df-154">You may delete the NuGet-specific elements in the folder.</span></span>

<span data-ttu-id="eb1df-155">En lista över NuGet element finns i [använda manuell hämtning för att hämta ett paket](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="eb1df-155">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb1df-156">Den manuella hämtningen innehåller inte några beroenden som krävs av modulen.</span><span class="sxs-lookup"><span data-stu-id="eb1df-156">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="eb1df-157">Om paketet har beroenden måste de installeras i systemet för att modulen ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="eb1df-157">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="eb1df-158">PowerShell-galleriet visar alla beroenden som krävs av paketet.</span><span class="sxs-lookup"><span data-stu-id="eb1df-158">The PowerShell Gallery shows all dependencies required by the package.</span></span>
