---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: ScriptAnalyzer regeln profil för galleriet
ms.openlocfilehash: 54100f7a530cbc769e4a0e2dbff18dbc5de88fa6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>ScriptAnalyzer regeln profil för galleriet

Om du vill kontrollera kvaliteten på objekt som publicerats i PowerShell-galleriet vi kör [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regler för att fastställa om det finns eventuella överträdelser i skript som har skickats.

Du hittar listan över regler som vi körs på ScriptAnalyzer [GitHub-sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Om du har frågor om reglerna vi kör kontakta PowerShell-galleriet administratörer, eller öppna ett problem för ScriptAnalzyer.

ScriptAnalyzer resultat visas på sidan varje enskilt objekt i galleriet i kommande utgåva. Vi rekommenderar att objektet ägare att kontrollera sina objekt att kontrollera att det finns inga allvarligt fel i publicerade objekt.
