---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: ff575ab56f07312658d111bccd7793b64ac071ea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a>ScriptAnazlyer regeln profil för galleriet
Om du vill kontrollera kvaliteten på objekt som publicerats i PowerShell-galleriet vi kör [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regler för att fastställa om det finns eventuella överträdelser i skript som har skickats.

Du hittar listan över regler som vi körs på ScriptAnalyzer [GitHub-sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Om du har frågor om reglerna vi kör kontakta PowerShell-galleriet administratörer, eller öppna ett problem för ScriptAnalzyer.

ScriptAnalyzer resultat visas på sidan varje enskilt objekt i galleriet i kommande utgåva. Vi rekommenderar att objektet ägare att kontrollera sina objekt att kontrollera att det finns inga allvarligt fel i publicerade objekt.