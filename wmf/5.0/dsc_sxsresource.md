---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218441"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="1438d-102">Sida-vid-sida-modulen versionshantering stöd för DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="1438d-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="1438d-103">Moduler som innehåller DSC-resurser kan vara installerade sida vid sida och DSC-konfigurationer kan använda en viss version av den resurs som är installerad på systemet.</span><span class="sxs-lookup"><span data-stu-id="1438d-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="1438d-104">Mer information finns i [av resurser med flera versioner](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="1438d-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="1438d-105">Kända problem</span><span class="sxs-lookup"><span data-stu-id="1438d-105">Known issues</span></span>

<span data-ttu-id="1438d-106">I den här versionen är följande kända problem i sida-vid-sida-installation:</span><span class="sxs-lookup"><span data-stu-id="1438d-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="1438d-107">Använder två olika versioner av DSC-resurs i samma konfiguration stöds inte.</span><span class="sxs-lookup"><span data-stu-id="1438d-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
