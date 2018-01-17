---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSCAutomationHostEnabled registernyckel
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
>Gäller för: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled registernyckel

DSC använder den **DSCAutomationHostEnabled** registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** att konfigurationen av datorn på första uppstart.
DSCAutomationHostEnabled stöder tre lägen:

|  DSCAutomationHostEnabled värde  |  Beskrivning   | 
|---|---| 
0 | Inaktivera konfigurerar datorn vid uppstart. |
1 | Aktivera konfigurerar datorn vid uppstart. |
2 | Aktivera konfigurerar datorn bara om DSC i väntande eller aktuella tillstånd. Det här är standardkonfigurationen. |

## <a name="see-also"></a>Se även

Ett exempel på hur du använder den här funktionen körs konfigurationer vid första uppstart finns [konfigurera en virtuella datorer på första uppstart med hjälp av DSC](bootstrapDsc.md).


