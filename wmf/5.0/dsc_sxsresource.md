---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: a565f2befddc32f5088fa3e158f58d2dd78d41b4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="34510-102">Sida-vid-sida-modulen versionshantering stöd för DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="34510-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="34510-103">Moduler som innehåller DSC-resurser kan vara installerade sida vid sida och DSC-konfigurationer kan använda en viss version av den resurs som är installerad på systemet.</span><span class="sxs-lookup"><span data-stu-id="34510-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="34510-104">Mer information finns i [av resurser med flera versioner](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="34510-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="34510-105">Kända problem</span><span class="sxs-lookup"><span data-stu-id="34510-105">Known issues</span></span>

<span data-ttu-id="34510-106">I den här versionen är följande kända problem i sida-vid-sida-installation:</span><span class="sxs-lookup"><span data-stu-id="34510-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="34510-107">Använder två olika versioner av DSC-resurs i samma konfiguration stöds inte.</span><span class="sxs-lookup"><span data-stu-id="34510-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>