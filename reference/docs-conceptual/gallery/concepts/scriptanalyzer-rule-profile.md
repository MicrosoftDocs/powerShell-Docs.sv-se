---
ms.date: 06/12/2017
title: Regel profil för ScriptAnalyzer för galleriet
description: Förklarar hur PowerShell-ScriptAnalyzer är integrerat med PowerShell-galleriet.
ms.openlocfilehash: 3af710e8811f0fabfb02f5317d5b4ff9c320f29a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646760"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Regel profil för ScriptAnalyzer för galleriet

För att säkerställa kvaliteten på paket som publiceras till PowerShell-galleriet, kör vi [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) -regler för att avgöra om det finns några överträdelser i de skript som skickas.

Du hittar listan över regler som vi kör på ScriptAnalyzer GitHub- [sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Om du har problem med reglerna som vi kör kontaktar du PowerShell-galleriet administratörer eller öppnar ett problem för ScriptAnalyzer.

ScriptAnalyzer-resultat visas på varje enskilt paket sida i galleriet i den kommande versionen. Vi uppmuntrar paket ägare att kontrol lera sina paket för att se till att det inte finns några allvarliga fel i publicerade paket.
