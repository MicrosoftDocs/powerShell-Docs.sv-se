---
ms.date: 12/11/2018
title: Paket med kompatibla PowerShell-utgåvor eller operativ system
description: Den här artikeln beskriver hur du söker i PowerShell-galleriet efter kompatibilitet med en speciell plattform eller utgåva.
ms.openlocfilehash: 9806c09c85febfd74bb69adf3d294fb4f559ff23
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661256"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Paket med kompatibla PowerShell-utgåvor eller operativ system

Från och med version 5,1 är PowerShell tillgängligt i olika utgåvor som kännetecknar varierande funktions uppsättningar och plattforms oberoende plattformar.

## <a name="searching-by-powershell-edition"></a>Söker efter PowerShell-utgåva

De två versionerna av PowerShell är:

- **Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.
- **Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>Med PowerShell-galleriet kan du filtrera paket som är kompatibla med vissa PowerShell-versioner

Om ett paket har kompatibla PSEditions anges de som en del av "PowerShell-versioner" på paketets visnings sida och även i paket resultat.
Du kan också söka efter kompatibla paket med PowerShell.

![Objekt visnings sidan med PSEditions](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Sök efter paket i galleriet för galleriet som fungerar på PowerShell-kärnan

Använd Taggar: "PSEdition_Desktop" och Taggar: "PSEdition_Core" för att filtrera paketen på PowerShell-galleriet.

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a>Använd Taggar: "PSEdition_Core" för att söka efter objekt som är kompatibla med PowerShell Core Edition

![Sök Resultat för objekt som är kompatibla med Core-PSEdition](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Använd Taggar: "PSEdition_Desktop" för att söka efter objekt som är kompatibla med PowerShell Desktop Edition

![Sök Resultat för objekt som är kompatibla med Desktop-PSEdition](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Sök efter paket för att hitta kompatibla utgåvor med PowerShell

Du kan ange taggar för att filtrera PowerShell-versionen och operativ systemet. Du använder `Find-Package` cmdleten som anger `-Tag` parametern för att ange den utgåva (och OS) som du är mål för. Gillar det här:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Söker efter operativ system

Eftersom PowerShell Core är tillgängligt för Windows, Linux och MacOS, kan paket i galleriet utformas för alla kombinationer av dessa operativ system. I galleriet Galleri använder du följande söktaggar för att hitta paket märkta med operativ system:

- Taggar: "Windows"
- Taggar: "Linux"
- Taggar: "MacOS"

Du kan ange taggarna på `Find-Module` (och andra cmdletar i PowerShellGet-modulen), så här:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Söker efter flera kompatibiliteter

Du kan söka efter ett paket som har flera-kompatibilitet med hjälp av syntaxen:

Taggar: "Compatibility1" "Compatibility2"

Om du till exempel söker efter ett paket med PowerShell-kompatibilitet som körs på både mina Windows-och Linux-datorer använder du Sök taggarna:

Taggar: "PSEdition_Core" Windows "" Linux "

Om du vill söka med PowerShell kan du använda `Find-Module` (och de andra cmdletarna i PowerShellGet-modulen), så här:

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Mer information om hur du redigerar och söker efter paket med kompatibla PowerShell-versioner

- [Moduler med PSEditions](../../concepts/module-psedition-support.md)
- [Skript med PSEditions](../../concepts/script-psedition-support.md)
