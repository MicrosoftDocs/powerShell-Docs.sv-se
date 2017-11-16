---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSCAutomationHostEnabled registernyckel
ms.openlocfilehash: e47c929b366f93738343eabc431aab5a4428352d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
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


