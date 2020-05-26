---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
ms.openlocfilehash: 0f35a798e5b7d51fdfb66e4e79ceab0e36ccea5b
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808341"
---
# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled-registernyckel

> Gäller för: Windows PowerShell 5,0

DSC använder register nyckeln **dscautomationhostenabled registernyckel** under **HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\policies\system** för att aktivera konfiguration av datorn vid första uppstarten.
**Dscautomationhostenabled registernyckel** stöder tre lägen:

|  Dscautomationhostenabled registernyckel-värde  |  Beskrivning   |
|---|---|
0 | Inaktivera konfigurering av datorn vid uppstart. |
1 | Aktivera konfigurering av datorn vid uppstart. |
2 | Aktivera endast konfigurering av datorn om DSC är i vänte läge eller aktuellt tillstånd. Detta är standardvärdet. |

## <a name="see-also"></a>Se även

Ett exempel på hur du använder den här funktionen för att köra konfigurationer vid första uppstarten finns i [Konfigurera en virtuell dator vid första uppstarten med hjälp av DSC](bootstrapDsc.md).
