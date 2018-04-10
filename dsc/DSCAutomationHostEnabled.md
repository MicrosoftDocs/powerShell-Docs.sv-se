---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
>Gäller för: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled-registernyckel

DSC använder den **DSCAutomationHostEnabled** registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** att konfigurationen av datorn på första uppstart.
DSCAutomationHostEnabled stöder tre lägen:

|  DSCAutomationHostEnabled värde  |  Beskrivning   |
|---|---|
0 | Inaktivera konfigurerar datorn vid uppstart. |
1 | Aktivera konfigurerar datorn vid uppstart. |
2 | Aktivera konfigurerar datorn bara om DSC i väntande eller aktuella tillstånd. Det här är standardkonfigurationen. |

## <a name="see-also"></a>Se även

Ett exempel på hur du använder den här funktionen körs konfigurationer vid första uppstart finns [konfigurera en virtuella datorer på första uppstart med hjälp av DSC](bootstrapDsc.md).