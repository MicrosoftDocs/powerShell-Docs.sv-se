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
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="d30e1-103">Regel profil för ScriptAnalyzer för galleriet</span><span class="sxs-lookup"><span data-stu-id="d30e1-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="d30e1-104">För att säkerställa kvaliteten på paket som publiceras till PowerShell-galleriet, kör vi [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) -regler för att avgöra om det finns några överträdelser i de skript som skickas.</span><span class="sxs-lookup"><span data-stu-id="d30e1-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="d30e1-105">Du hittar listan över regler som vi kör på ScriptAnalyzer GitHub- [sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="d30e1-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="d30e1-106">Om du har problem med reglerna som vi kör kontaktar du PowerShell-galleriet administratörer eller öppnar ett problem för ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="d30e1-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="d30e1-107">ScriptAnalyzer-resultat visas på varje enskilt paket sida i galleriet i den kommande versionen.</span><span class="sxs-lookup"><span data-stu-id="d30e1-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="d30e1-108">Vi uppmuntrar paket ägare att kontrol lera sina paket för att se till att det inte finns några allvarliga fel i publicerade paket.</span><span class="sxs-lookup"><span data-stu-id="d30e1-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
