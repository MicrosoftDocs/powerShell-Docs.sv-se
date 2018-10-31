---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Paket med kompatibla PowerShell-utgåvor
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004153"
---
# <a name="packages-with-compatible-powershell-editions"></a><span data-ttu-id="1f55d-103">Paket med kompatibla PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="1f55d-103">Packages with compatible PowerShell Editions</span></span>

<span data-ttu-id="1f55d-104">Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="1f55d-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="1f55d-105">**Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="1f55d-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="1f55d-106">**Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="1f55d-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="1f55d-107">PowerShell-galleriet extraherar stöds PSEditions metadata och kan du filter paket som kompatibla för specifika PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="1f55d-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="1f55d-108">Om ett paket har kompatibla anges PSEditions de listas som en del av PowerShell-utgåvor på sidan paket och på paket resultat.</span><span class="sxs-lookup"><span data-stu-id="1f55d-108">If a package has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>

![Visa objekt sida med PSEditions](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="1f55d-110">Sök efter paket i Användargränssnittet som fungerar på PowerShellCore-galleriet</span><span class="sxs-lookup"><span data-stu-id="1f55d-110">Search for packages in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="1f55d-111">Använd taggar: ”PSEdition_Desktop” och taggar: ”PSEdition_Core” till filter paketen på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="1f55d-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="1f55d-112">Använd taggar: ”PSEdition_Core” söker efter objekt som är kompatibel med PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="1f55d-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Sökresultat för objekt som är kompatibla med grundläggande PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="1f55d-114">Använd taggar: ”PSEdition_Desktop” söker efter objekt som är kompatibel med PowerShell Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="1f55d-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Sökresultat för objekt som är kompatibel med Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="1f55d-116">Mer information om redigering och söka efter paket med kompatibla PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="1f55d-116">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="1f55d-117">Moduler med PSEditions</span><span class="sxs-lookup"><span data-stu-id="1f55d-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="1f55d-118">Skript med PSEditions</span><span class="sxs-lookup"><span data-stu-id="1f55d-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
