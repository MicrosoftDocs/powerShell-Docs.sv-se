---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: galleriet, powershell, cmdlet, psgallery
title: Paket med operativsystemet eller kompatibla PowerShell-utgåvor
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685958"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Paket med kompatibla PowerShell-utgåvor eller operativsystem

Från och med version 5.1 finns finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformen enhetskompatibilitet i hela.

## <a name="searching-by-powershell-edition"></a>Söka efter PowerShell-utgåva 
Det finns två versioner av Powershell:
- **Desktop Edition:** Bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows-skrivbordet.
- **Core Edition:** Bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell-galleriet kan du filtrera paket som är kompatibel för specifika PowerShell-utgåvor

Om ett paket har kompatibla anges PSEditions de listas som en del av PowerShell-utgåvor på sidan paket och på paket resultat.
Du kan också söka efter kompatibla paket med hjälp av PowerShell.

![Visa objekt sida med PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Sök efter paket i galleriet Användargränssnittet som fungerar i PowerShell Core

Använd taggar: ”PSEdition_Desktop” och taggar: ”PSEdition_Core” till filter paketen på PowerShell-galleriet.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Använd taggar: ”PSEdition_Core” söker efter objekt som är kompatibel med PowerShell Core Edition.

![Sökresultat för objekt som är kompatibla med grundläggande PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Använd taggar: ”PSEdition_Desktop” söker efter objekt som är kompatibel med PowerShell Desktop Edition.

![Sökresultat för objekt som är kompatibel med Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Sök efter paket för att hitta kompatibla versioner med hjälp av PowerShell
Du kan ange taggar om du vill filtrera för PowerShell-utgåva och operativsystem. Du använder den `Find-Package` cmdlet att ange den `-Tag` parametern för att ange edition (och OS) du arbetar med.
Gillar det här:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Söker efter operativsystem 

Eftersom PowerShell Core är tillgänglig för Windows, Linux och MacOS kan-paket i galleriet utformas för valfri kombination av dessa operativsystem. Använd följande taggar om searchs för att hitta paket som taggats med operativsystemet i galleriet Användargränssnittet:

- Taggar: "Windows"
- Taggar: "Linux"
- Taggar: "MacOS" 

Du kan ange dessa taggar på `Find-Module` (och andra cmdlets i modulen PowerShellGet), så här:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Söker efter flera enhetskompatibilitet i hela

Du kan se ut för ett paket som har flera enhetskompatibilitet i hela med hjälp av syntaxen: 

Taggar: ”Compatibility1” ”Compatibility2” 

Till exempel om du letar efter ett paket med PowerShell Core kompatibilitet som körs på både min Windows- och Linux-datorer, Använd söktaggar:

Taggar: "PSEdition_Core" "Windows" "Linux" 

Om du vill söka med hjälp av PowerShell, kan du använda den `Find-Module` (och andra cmdlets i modulen PowerShellGet), så här:

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Mer information om redigering och söka efter paket med kompatibla PowerShell-utgåvor

- [Moduler med PSEditions](../../concepts/module-psedition-support.md)
- [Skript med PSEditions](../../concepts/script-psedition-support.md)
