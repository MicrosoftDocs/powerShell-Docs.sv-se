---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_pseditions
ms.openlocfilehash: 0b30c1da53832a6b74be7aa14ed9331b1e9fe643
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="fb3f6-103">Objekt med kompatibla versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb3f6-103">Items with compatible PowerShell Editions</span></span>
<span data-ttu-id="fb3f6-104">Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="fb3f6-105">**Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="fb3f6-106">**Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="fb3f6-107">PowerShell-galleriet extraherar stöds PSEditions metadata och låter dig filter objekten kompatibel för specifika versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb3f6-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="fb3f6-108">Om ett objekt har kompatibla anges PSEditions visas som en del av PowerShell-versioner i sidan objektet och i objekt resultat.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>
<span data-ttu-id="fb3f6-109">![Visa objekt sida med PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)</span><span class="sxs-lookup"><span data-stu-id="fb3f6-109">![Item display page with PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)</span></span>

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="fb3f6-110">Sök efter objekt i galleriet användargränssnitt som fungerar på PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="fb3f6-110">Search for items in the gallery UI which works on PowerShellCore</span></span>
<span data-ttu-id="fb3f6-111">Använd taggar: ”PSEdition_Desktop” och taggar: ”PSEdition_Core” till filter objekten på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="fb3f6-112">Använd taggar: ”PSEdition_Core” för att söka efter objekt som är kompatibel med PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>
![Sökresultat för objekt som är kompatibel med Core PSEdition](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="fb3f6-114">Använd taggar: ”PSEdition_Desktop” för att söka efter objekt som är kompatibel med PowerShell Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="fb3f6-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>
![Sökresultat för objekt som är kompatibel med fjärrskrivbord PSEdition](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="fb3f6-116">Mer information om redigering och söka efter objekt med kompatibla versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb3f6-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[<span data-ttu-id="fb3f6-117">Moduler med PSEditions</span><span class="sxs-lookup"><span data-stu-id="fb3f6-117">Modules with PSEditions</span></span>](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[<span data-ttu-id="fb3f6-118">Skript med PSEditions</span><span class="sxs-lookup"><span data-stu-id="fb3f6-118">Scripts with PSEditions</span></span>](../psget/script/scriptwithpseditionsupport.md)