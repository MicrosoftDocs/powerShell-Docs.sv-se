---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_pseditions
ms.openlocfilehash: 6634da5c2dadee9c0c6470b3d3e8883e6d02160f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="items-with-compatible-powershell-editions"></a>Objekt med kompatibla versioner av PowerShell
Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.

- **Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.
- **Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>PowerShell-galleriet extraherar stöds PSEditions metadata och låter dig filter objekten kompatibel för specifika versioner av PowerShell

Om ett objekt har kompatibla anges PSEditions visas som en del av PowerShell-versioner i sidan objektet och i objekt resultat.
![Visa objekt sida med PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Sök efter objekt i galleriet användargränssnitt som fungerar på PowerShellCore
Använd taggar: ”PSEdition_Desktop” och taggar: ”PSEdition_Core” till filter objekten på PowerShell-galleriet.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Använd taggar: ”PSEdition_Core” för att söka efter objekt som är kompatibel med PowerShell Core Edition.
![Sökresultat för objekt som är kompatibel med Core PSEdition](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Använd taggar: ”PSEdition_Desktop” för att söka efter objekt som är kompatibel med PowerShell Desktop Edition.
![Sökresultat för objekt som är kompatibel med fjärrskrivbord PSEdition](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Mer information om redigering och söka efter objekt med kompatibla versioner av PowerShell
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[Moduler med PSEditions](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[Skript med PSEditions](../psget/script/scriptwithpseditionsupport.md)

