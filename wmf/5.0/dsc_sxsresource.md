---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Sida-vid-sida-modulen versionshantering stöd för DSC-resurser

Moduler som innehåller DSC-resurser kan vara installerade sida vid sida och DSC-konfigurationer kan använda en viss version av den resurs som är installerad på systemet.

Mer information finns i [av resurser med flera versioner](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Kända problem

I den här versionen är följande kända problem i sida-vid-sida-installation:

-   Använder två olika versioner av DSC-resurs i samma konfiguration stöds inte.

