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
# <a name="packages-with-compatible-powershell-editions"></a>Paket med kompatibla PowerShell-utgåvor

Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.

- **Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.
- **Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a>PowerShell-galleriet extraherar stöds PSEditions metadata och kan du filter paket som kompatibla för specifika PowerShell-utgåvor

Om ett paket har kompatibla anges PSEditions de listas som en del av PowerShell-utgåvor på sidan paket och på paket resultat.

![Visa objekt sida med PSEditions](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a>Sök efter paket i Användargränssnittet som fungerar på PowerShellCore-galleriet

Använd taggar: ”PSEdition_Desktop” och taggar: ”PSEdition_Core” till filter paketen på PowerShell-galleriet.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Använd taggar: ”PSEdition_Core” söker efter objekt som är kompatibel med PowerShell Core Edition.

![Sökresultat för objekt som är kompatibla med grundläggande PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Använd taggar: ”PSEdition_Desktop” söker efter objekt som är kompatibel med PowerShell Desktop Edition.

![Sökresultat för objekt som är kompatibel med Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Mer information om redigering och söka efter paket med kompatibla PowerShell-utgåvor

- [Moduler med PSEditions](../../concepts/module-psedition-support.md)
- [Skript med PSEditions](../../concepts/script-psedition-support.md)
