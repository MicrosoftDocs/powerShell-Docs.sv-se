---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: ScriptAnalyzer regeln profil för galleriet
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084597"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>ScriptAnalyzer regeln profil för galleriet

För att säkerställa kvaliteten på paket som publicerats till PowerShell-galleriet, vi kör [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regler för att avgöra om det finns eventuella överträdelser i skripten har skickats.

Du hittar listan över regler som ska köras på ScriptAnalyzer [GitHub-sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Om du har frågor om reglerna är igång kan kontakta administratörer för PowerShell-galleriet, eller öppna ett ärende för ScriptAnalyzer.

ScriptAnalyzer resultat visas på sidorna enskilda paket i galleriet i den kommande versionen. Vi rekommenderar att paketet ägare att kontrollera sina paket för att kontrollera att det finns inga allvarliga fel i publicerade paket.
