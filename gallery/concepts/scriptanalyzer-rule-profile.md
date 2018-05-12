---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: ScriptAnazlyer regeln profil för galleriet
ms.openlocfilehash: 74eab49e4c4a546655451ef21b30cfcafaeb9584
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a>ScriptAnazlyer regeln profil för galleriet

Om du vill kontrollera kvaliteten på objekt som publicerats i PowerShell-galleriet vi kör [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regler för att fastställa om det finns eventuella överträdelser i skript som har skickats.

Du hittar listan över regler som vi körs på ScriptAnalyzer [GitHub-sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Om du har frågor om reglerna vi kör kontakta PowerShell-galleriet administratörer, eller öppna ett problem för ScriptAnalzyer.

ScriptAnalyzer resultat visas på sidan varje enskilt objekt i galleriet i kommande utgåva. Vi rekommenderar att objektet ägare att kontrollera sina objekt att kontrollera att det finns inga allvarligt fel i publicerade objekt.