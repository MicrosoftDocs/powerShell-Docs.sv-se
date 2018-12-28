---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Windows PowerShell Desired State Configuration-översikt
ms.openlocfilehash: 3e4f0afa17ab60bfa98f1b86b9830462a7c8e1cf
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405267"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell Desired State Configuration-översikt

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC är en plattform för hantering i PowerShell som gör det möjligt för dig att hantera IT-avdelningen och infrastruktur för utveckling med konfiguration som kod.

- En översikt över fördelarna med hjälp av DSC finns i [Desired State Configuration-översikt för beslutsfattare](decisionMaker.md).
- En översikt över tekniska fördelarna med att använda DSC finns i [Desired State Configuration-översikt för tekniker](DscForEngineers.md).
- Om du vill börja med DSC snabbt se [DSC-Snabbstart](../quickstarts/website-quickstart.md).

## <a name="key-concepts"></a>Viktiga begrepp

DSC är en deklarativ plattform som används för konfiguration, distribution och hantering av system. Det består av tre huvudkomponenter:

- [Konfigurationer](../configurations/configurations.md) deklarativ PowerShell-skript som definiera och konfigurera instanser av resurser.
    Vid kör konfigurationen, DSC (och de resurser som anropas av konfigurationen) kommer kontrollerar helt enkelt ”gör den det”, att systemet finns i tillståndet anges av konfigurationen.
    DSC-konfigurationer är också idempotenta: den lokala Configuration Manager (LCM) fortsätter att se till att datorer konfigureras i det tillstånd konfigurationen deklarerar.
- [Resurser](../resources/resources.md) DSC ”gör den det” tillhör. De innehåller kod som placerar och Behåll mål för en konfiguration i det angivna tillståndet.
    Resurser finns i PowerShell-moduler och kan skrivas till modellera något som allmän som en fil eller en Windows-process eller så specifik som en IIS-server eller en virtuell dator som körs i Azure.
- Den [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md) är motorn som underlättar DSC interaktionen mellan resurser och konfigurationer.
    LCM söker regelbundet systemet använder Kontrollflöde som implementeras av resurser för att säkerställa att tillståndet som definieras av en konfiguration upprätthålls.
    Om systemet har slut på tillstånd, gör LCM anrop till koden i resurser för att ”gör den det” enligt konfigurationen.

## <a name="see-also"></a>Se även

- [DSC-konfigurationer](../configurations/configurations.md)
- [DSC-resurser](../resources/resources.md)
- [Konfigurera den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md)
