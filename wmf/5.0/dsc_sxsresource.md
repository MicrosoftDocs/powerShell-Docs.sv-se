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
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Sida-vid-sida-modulen versionshantering stöd för DSC-resurser

Moduler som innehåller DSC-resurser kan vara installerade sida vid sida och DSC-konfigurationer kan använda en viss version av den resurs som är installerad på systemet.

Mer information finns i [av resurser med flera versioner](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Kända problem

I den här versionen är följande kända problem i sida-vid-sida-installation:

-   Använder två olika versioner av DSC-resurs i samma konfiguration stöds inte.