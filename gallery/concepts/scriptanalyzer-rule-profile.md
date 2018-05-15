---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: ScriptAnazlyer regeln profil för galleriet
ms.openlocfilehash: 74eab49e4c4a546655451ef21b30cfcafaeb9584
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a><span data-ttu-id="b68c6-103">ScriptAnazlyer regeln profil för galleriet</span><span class="sxs-lookup"><span data-stu-id="b68c6-103">ScriptAnazlyer rule profile for Gallery</span></span>

<span data-ttu-id="b68c6-104">Om du vill kontrollera kvaliteten på objekt som publicerats i PowerShell-galleriet vi kör [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regler för att fastställa om det finns eventuella överträdelser i skript som har skickats.</span><span class="sxs-lookup"><span data-stu-id="b68c6-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="b68c6-105">Du hittar listan över regler som vi körs på ScriptAnalyzer [GitHub-sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="b68c6-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="b68c6-106">Om du har frågor om reglerna vi kör kontakta PowerShell-galleriet administratörer, eller öppna ett problem för ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="b68c6-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="b68c6-107">ScriptAnalyzer resultat visas på sidan varje enskilt objekt i galleriet i kommande utgåva.</span><span class="sxs-lookup"><span data-stu-id="b68c6-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="b68c6-108">Vi rekommenderar att objektet ägare att kontrollera sina objekt att kontrollera att det finns inga allvarligt fel i publicerade objekt.</span><span class="sxs-lookup"><span data-stu-id="b68c6-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>