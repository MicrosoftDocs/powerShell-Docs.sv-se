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
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="5635f-103">Regel profil för ScriptAnalyzer för galleriet</span><span class="sxs-lookup"><span data-stu-id="5635f-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="5635f-104">För att säkerställa kvaliteten på paket som publiceras till PowerShell-galleriet, kör vi [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) -regler för att avgöra om det finns några överträdelser i de skript som skickas.</span><span class="sxs-lookup"><span data-stu-id="5635f-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="5635f-105">Du hittar listan över regler som vi kör på ScriptAnalyzer GitHub- [sidan](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="5635f-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="5635f-106">Om du har problem med reglerna som vi kör kontaktar du PowerShell-galleriet administratörer eller öppnar ett problem för ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="5635f-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="5635f-107">ScriptAnalyzer-resultat visas på varje enskilt paket sida i galleriet i den kommande versionen.</span><span class="sxs-lookup"><span data-stu-id="5635f-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="5635f-108">Vi uppmuntrar paket ägare att kontrol lera sina paket för att se till att det inte finns några allvarliga fel i publicerade paket.</span><span class="sxs-lookup"><span data-stu-id="5635f-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
