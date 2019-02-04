---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685636"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="fd247-102">Stöd för versionshantering sida-vid-sida-modulen för DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="fd247-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="fd247-103">Moduler som innehåller DSC-resurser kan vara installerade sida-vid-sida och DSC-konfigurationer kan använda en specifik version av den resurs som är installerad på systemet.</span><span class="sxs-lookup"><span data-stu-id="fd247-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="fd247-104">Mer information finns i [av resurser med flera versioner](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="fd247-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="fd247-105">Kända problem</span><span class="sxs-lookup"><span data-stu-id="fd247-105">Known issues</span></span>

<span data-ttu-id="fd247-106">I den här versionen har är följande kända problem i sida-vid-sida-installation:</span><span class="sxs-lookup"><span data-stu-id="fd247-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="fd247-107">Använder två olika versioner av DSC-resurs i samma konfiguration stöds inte.</span><span class="sxs-lookup"><span data-stu-id="fd247-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
