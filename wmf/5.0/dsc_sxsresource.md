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
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Sida-vid-sida-modulen versionshantering stöd för DSC-resurser

Moduler som innehåller DSC-resurser kan vara installerade sida vid sida och DSC-konfigurationer kan använda en viss version av den resurs som är installerad på systemet.

Mer information finns i [av resurser med flera versioner](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Kända problem

I den här versionen är följande kända problem i sida-vid-sida-installation:

-   Använder två olika versioner av DSC-resurs i samma konfiguration stöds inte.
