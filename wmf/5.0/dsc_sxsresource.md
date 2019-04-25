---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057935"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Stöd för versionshantering sida-vid-sida-modulen för DSC-resurser

Moduler som innehåller DSC-resurser kan vara installerade sida-vid-sida och DSC-konfigurationer kan använda en specifik version av den resurs som är installerad på systemet.

Mer information finns i [av resurser med flera versioner](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Kända problem

I den här versionen har är följande kända problem i sida-vid-sida-installation:

-   Använder två olika versioner av DSC-resurs i samma konfiguration stöds inte.
