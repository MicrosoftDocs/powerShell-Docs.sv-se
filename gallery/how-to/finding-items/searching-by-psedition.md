---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Objekt med kompatibla versioner av PowerShell
ms.openlocfilehash: f661c2cd076acb9c11394ba0b752ebd154965ff4
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="5aca5-103">Objekt med kompatibla versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="5aca5-103">Items with compatible PowerShell Editions</span></span>

<span data-ttu-id="5aca5-104">Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="5aca5-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="5aca5-105">**Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="5aca5-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="5aca5-106">**Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="5aca5-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="5aca5-107">PowerShell-galleriet extraherar stöds PSEditions metadata och låter dig filter objekten kompatibel för specifika versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="5aca5-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="5aca5-108">Om ett objekt har kompatibla anges PSEditions visas som en del av PowerShell-versioner i sidan objektet och i objekt resultat.</span><span class="sxs-lookup"><span data-stu-id="5aca5-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>

![Visa objekt sida med PSEditions](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="5aca5-110">Sök efter objekt i galleriet användargränssnitt som fungerar på PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="5aca5-110">Search for items in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="5aca5-111">Använd taggar: ”PSEdition_Desktop” och taggar: ”PSEdition_Core” till filter objekten på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="5aca5-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="5aca5-112">Använd taggar: ”PSEdition_Core” för att söka efter objekt som är kompatibel med PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="5aca5-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Sökresultat för objekt som är kompatibel med Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="5aca5-114">Använd taggar: ”PSEdition_Desktop” för att söka efter objekt som är kompatibel med PowerShell Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="5aca5-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Sökresultat för objekt som är kompatibel med fjärrskrivbord PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="5aca5-116">Mer information om redigering och söka efter objekt med kompatibla versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="5aca5-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="5aca5-117">Moduler med PSEditions</span><span class="sxs-lookup"><span data-stu-id="5aca5-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="5aca5-118">Skript med PSEditions</span><span class="sxs-lookup"><span data-stu-id="5aca5-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)