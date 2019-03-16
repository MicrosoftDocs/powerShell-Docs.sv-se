---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: ScriptAnalyzer regeln profil för galleriet
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059600"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="e4d09-103">ScriptAnalyzer regeln profil för galleriet</span><span class="sxs-lookup"><span data-stu-id="e4d09-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="e4d09-104">För att säkerställa kvaliteten på paket som publicerats till PowerShell-galleriet, vi kör [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regler för att avgöra om det finns eventuella överträdelser i skripten har skickats.</span><span class="sxs-lookup"><span data-stu-id="e4d09-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="e4d09-105">Du hittar listan över regler som ska köras på ScriptAnalyzer [GitHub-sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="e4d09-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="e4d09-106">Om du har frågor om reglerna är igång kan kontakta administratörer för PowerShell-galleriet, eller öppna ett ärende för ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="e4d09-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="e4d09-107">ScriptAnalyzer resultat visas på sidorna enskilda paket i galleriet i den kommande versionen.</span><span class="sxs-lookup"><span data-stu-id="e4d09-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="e4d09-108">Vi rekommenderar att paketet ägare att kontrollera sina paket för att kontrollera att det finns inga allvarliga fel i publicerade paket.</span><span class="sxs-lookup"><span data-stu-id="e4d09-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
