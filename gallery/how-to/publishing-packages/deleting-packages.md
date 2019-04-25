---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Ta bort paket
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084172"
---
# <a name="deleting-packages"></a><span data-ttu-id="33e58-103">Ta bort paket</span><span class="sxs-lookup"><span data-stu-id="33e58-103">Deleting Packages</span></span>

<span data-ttu-id="33e58-104">PowerShell-galleriet har inte stöd för permanent borttagning av paket, eftersom som skulle skapa vem som helst som beroende av den återstående tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="33e58-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="33e58-105">I stället PowerShell-galleriet har stöd för ett sätt att ”ta bort” ett paket, det kan du göra på sidan för hantering av paketet på webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="33e58-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="33e58-106">När ett paket inte visas, visas den inte längre i sökningar och i alla paket lista, både på PowerShell-galleriet och använder PowerShellGet-kommandon.</span><span class="sxs-lookup"><span data-stu-id="33e58-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="33e58-107">Emellertid nedladdningsbara genom att ange den exakta versionen, vilket kan de automatiserade skript för att fortsätta arbeta.</span><span class="sxs-lookup"><span data-stu-id="33e58-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="33e58-108">Om du stöter på särskilda omständigheter där du tror att någon av dina paket måste tas bort, kan det hanteras manuellt av PowerShell-galleriet-teamet.</span><span class="sxs-lookup"><span data-stu-id="33e58-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="33e58-109">Om det finns en upphovsrättsintrång problemet eller potentiellt skadliga innehåll, som till exempel vara en giltig orsak till att ta bort den.</span><span class="sxs-lookup"><span data-stu-id="33e58-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="33e58-110">Du bör skicka en supportbegäran via [PowerShell-galleriet](http://www.PowerShellGallery.com) i så fall.</span><span class="sxs-lookup"><span data-stu-id="33e58-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>
