---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076503"
---
>Gäller för: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled-registernyckel

DSC-använder den **DSCAutomationHostEnabled** registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** att konfigurationen av dator vid första uppstart.
**DSCAutomationHostEnabled** stöder tre lägen:

|  DSCAutomationHostEnabled-värde  |  Beskrivning   |
|---|---|
0 | Inaktivera konfigurerar datorn vid uppstart. |
1 | Aktivera konfigurerar datorn vid uppstart. |
2 | Aktivera konfigurerar datorn endast om DSC är i väntande eller aktuella tillstånd. Detta är standardvärdet. |

## <a name="see-also"></a>Se även

Ett exempel på hur du använder den här funktionen körs konfigurationer vid första uppstart finns i [konfigurera en virtuell dator vid första uppstart med hjälp av DSC](bootstrapDsc.md).
