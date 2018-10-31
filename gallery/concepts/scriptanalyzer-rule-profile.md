---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: ScriptAnalyzer regeln profil för galleriet
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002504"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>ScriptAnalyzer regeln profil för galleriet

För att säkerställa kvaliteten på paket som publicerats till PowerShell-galleriet, vi kör [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regler för att avgöra om det finns eventuella överträdelser i skripten har skickats.

Du hittar listan över regler som ska köras på ScriptAnalyzer [GitHub-sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Om du har frågor om reglerna är igång kan kontakta administratörer för PowerShell-galleriet, eller öppna ett ärende för ScriptAnalzyer.

ScriptAnalyzer resultat visas på sidorna enskilda paket i galleriet i den kommande versionen. Vi rekommenderar att paketet ägare att kontrollera sina paket för att kontrollera att det finns inga allvarliga fel i publicerade paket.
