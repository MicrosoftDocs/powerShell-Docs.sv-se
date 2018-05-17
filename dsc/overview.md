---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Windows PowerShell Desired State Configuration-översikt
ms.openlocfilehash: c9069d7c9ce9c614330e36a42233b00363660a4b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell Desired State Configuration-översikt

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC är en plattform i PowerShell som gör det möjligt för dig att hantera IT-ADMINISTRATÖREN och utveckling infrastruktur med konfiguration som kod.

- En översikt över företagets fördelar med hjälp av DSC, se [Desired Configuration översikt över för beslutsfattare](decisionMaker.md).
- En översikt över engineering fördelarna med att använda DSC, se [Desired Configuration översikt över för Engineers](DscForEngineers.md).
- Om du vill börja använda DSC snabbt, se [DSC Snabbstart](quickStart.md).

## <a name="key-concepts"></a>Viktiga begrepp

DSC är en deklarativ plattform som används för konfiguration, distribution och hantering av system. Det består av tre huvudkomponenter:

- [Konfigurationer](configurations.md) är deklarativ PowerShell-skript som definierar och konfigurerar instanser av resurser.
    Vid konfigurationen, DSC (och resurser som anropas av konfigurationen) kommer helt enkelt ”gör det så”, se till att systemet finns i tillståndet utvecklas av konfigurationen.
    DSC-konfigurationer är också idempotent: den lokala Configuration Manager (MGM) kommer att fortsätta att säkerställa att datorer har konfigurerats på det tillstånd konfigurationen deklarerar.
- [Resurser](resources.md) DSC ”gör den det” tillhör. De innehåller koden som placeras och hålla målet för en konfiguration i det angivna tillståndet.
    Resurser finns i PowerShell-moduler och kan skrivas till modellen är något som allmänt som en fil eller en Windows-process eller så specifik som en IIS-server eller en virtuell dator som körs i Azure.
- Den [lokala Configuration Manager (MGM)](metaConfig.md) är motorn som underlättar DSC interaktionen mellan resurser och konfigurationer.
    MGM genomsöker regelbundet systemet använder Kontrollflöde som implementeras av resurser för att säkerställa att tillståndet som definierats av en upprätthålls.
    Om systemet har slut på tillstånd, anropar MGM koden i resurser för att ”gör den det” enligt konfigurationen.

## <a name="see-also"></a>Se även

- [DSC-konfigurationer](configurations.md)
- [DSC-resurser](resources.md)
- [Konfigurera den lokala Configuration Manager](metaConfig.md)