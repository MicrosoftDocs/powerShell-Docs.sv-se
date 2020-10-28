---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
description: Den här artikeln definierar de värden som kan anges i register nyckeln Dscautomationhostenabled registernyckel
ms.openlocfilehash: 50f752dd882e9b0787ed4a4cbc22731fc1d608f5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656186"
---
# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled-registernyckel

> Gäller för: Windows PowerShell 5,0

DSC använder register nyckeln **dscautomationhostenabled registernyckel** under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** för att aktivera konfiguration av datorn vid första start. **Dscautomationhostenabled registernyckel** stöder tre lägen:

| Dscautomationhostenabled registernyckel-värde |                                              Beskrivning                                              |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| 0                              | Inaktivera konfigurering av datorn vid uppstart.                                                           |
| 1                              | Aktivera konfigurering av datorn vid uppstart.                                                            |
| 2                              | Aktivera endast konfigurering av datorn om DSC är i vänte läge eller aktuellt tillstånd. Detta är standardvärdet. |

## <a name="see-also"></a>Se även

Ett exempel på hur du använder den här funktionen för att köra konfigurationer vid första uppstarten finns i [Konfigurera en virtuell dator vid första uppstarten med hjälp av DSC](bootstrapDsc.md).
