---
ms.date: 06/12/2017
title: Ta bort paket från PowerShell-galleriet
description: Ta bort paket från PowerShell-galleriet
ms.openlocfilehash: e02fad61ce8ab808ba9fdf4ab16b9ae236a49e80
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662570"
---
# <a name="deleting-packages"></a><span data-ttu-id="4e52f-103">Ta bort paket</span><span class="sxs-lookup"><span data-stu-id="4e52f-103">Deleting Packages</span></span>

<span data-ttu-id="4e52f-104">PowerShell-galleriet har inte stöd för permanent borttagning av paket, eftersom det skulle bryta alla som är beroende av den återstående tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="4e52f-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="4e52f-105">I stället har PowerShell-galleriet stöd för ett-paket, som kan göras på sidan paket hantering på webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="4e52f-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span> <span data-ttu-id="4e52f-106">När ett paket inte visas i listan visas det inte längre i Sök och i någon paket lista, både på PowerShell-galleriet och med PowerShellGet-kommandon.</span><span class="sxs-lookup"><span data-stu-id="4e52f-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="4e52f-107">Men det är fortfarande nedladdnings Bart genom att ange dess exakta version, vilket är det som tillåter att de automatiserade skripten fortsätter att fungera.</span><span class="sxs-lookup"><span data-stu-id="4e52f-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="4e52f-108">Om du stöter på en situation där du tror att ett av dina paket måste tas bort, kan det hanteras manuellt av PowerShell-galleriets teamet.</span><span class="sxs-lookup"><span data-stu-id="4e52f-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span> <span data-ttu-id="4e52f-109">Om det till exempel finns ett problem med upphovs rätts intrång eller potentiellt skadligt innehåll, kan det vara en giltig anledning att ta bort den.</span><span class="sxs-lookup"><span data-stu-id="4e52f-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span> <span data-ttu-id="4e52f-110">Du bör skicka in en support förfrågan via [PowerShell-galleriet](https://www.PowerShellGallery.com) i detta fall.</span><span class="sxs-lookup"><span data-stu-id="4e52f-110">You should submit a support request through [PowerShell Gallery](https://www.PowerShellGallery.com) in that case.</span></span>
