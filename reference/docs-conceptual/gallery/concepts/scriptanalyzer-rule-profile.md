---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Regel profil för ScriptAnalyzer för galleriet
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71329171"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Regel profil för ScriptAnalyzer för galleriet

För att säkerställa kvaliteten på paket som publiceras till PowerShell-galleriet, kör vi [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) -regler för att avgöra om det finns några överträdelser i de skript som skickas.

Du hittar listan över regler som vi kör på ScriptAnalyzer GitHub- [sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Om du har problem med reglerna som vi kör kontaktar du PowerShell-galleriet administratörer eller öppnar ett problem för ScriptAnalyzer.

ScriptAnalyzer-resultat visas på varje enskilt paket sida i galleriet i den kommande versionen. Vi uppmuntrar paket ägare att kontrol lera sina paket för att se till att det inte finns några allvarliga fel i publicerade paket.
