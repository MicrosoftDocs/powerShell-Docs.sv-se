---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942169"
---
>Gäller för: Windows PowerShell 5,0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled-registernyckel

DSC använder register nyckeln **dscautomationhostenabled registernyckel** under **HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\policies\system** för att aktivera konfiguration av datorn vid första uppstarten.
**Dscautomationhostenabled registernyckel** stöder tre lägen:

|  Dscautomationhostenabled registernyckel-värde  |  Beskrivning   |
|---|---|
0 | Inaktivera konfigurering av datorn vid uppstart. |
1 | Aktivera konfigurering av datorn vid uppstart. |
2 | Aktivera endast konfigurering av datorn om DSC är i vänte läge eller aktuellt tillstånd. Detta är standardvärdet. |

## <a name="see-also"></a>Se även

Ett exempel på hur du använder den här funktionen för att köra konfigurationer vid första uppstarten finns i [Konfigurera en virtuell dator vid första uppstarten med hjälp av DSC](bootstrapDsc.md).
