---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Översikt över önskad tillstånds konfiguration i Windows PowerShell
ms.openlocfilehash: 5c4853cb059ca0cf063a9450f97230732bc56b10
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941728"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Översikt över önskad tillstånds konfiguration i Windows PowerShell

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

DSC är en hanterings plattform i PowerShell som gör att du kan hantera din IT-och utvecklings infrastruktur med konfiguration som kod.

- En översikt över affärs fördelarna med att använda DSC finns i [Översikt över önskad tillstånds konfiguration för besluts fattare](decisionMaker.md).
- En översikt över de tekniska fördelarna med att använda DSC finns i [Översikt över önskad tillstånds konfiguration för tekniker](DscForEngineers.md).
- Information om hur du börjar använda DSC snabbt finns i [snabb start för DSC](../quickstarts/website-quickstart.md).

## <a name="key-concepts"></a>Viktiga begrepp

DSC är en deklarativ plattform som används för konfiguration, distribution och hantering av system. Det består av tre primära komponenter:

- [Konfigurationer](../configurations/configurations.md) är deklarativ PowerShell-skript som definierar och konfigurerar instanser av resurser.
    När du kör konfigurationen blir DSC (och de resurser som anropas av konfigurationen) bara "gör det så", vilket säkerställer att systemet finns i det tillstånd som anges av konfigurationen.
    DSC-konfigurationer är också idempotenta: den lokala Configuration Manager (LCM) fortsätter att se till att datorerna är konfigurerade i det tillstånd som konfigurationen deklarerar.
- [Resurser](../resources/resources.md) är "gör det så att det är en del av DSC. De innehåller koden som anger och behåller målet för en konfiguration i det angivna läget.
    Resurser finns i PowerShell-moduler och kan skrivas för att modellera saker som generiska som en fil eller en Windows-process, eller som är särskilt en IIS-server eller en virtuell dator som körs i Azure.
- Den [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md) är den motor som används av DSC för att förenkla interaktionen mellan resurser och konfigurationer.
    LCM avsöker regelbundet systemet med hjälp av kontroll flödet som implementeras av resurser för att säkerställa att det tillstånd som definieras av en konfiguration upprätthålls.
    Om systemet inte är i rätt tillstånd, gör LCM anrop till koden i resurser för att "göra det" enligt konfigurationen.

## <a name="see-also"></a>Se även

- [DSC-konfigurationer](../configurations/configurations.md)
- [DSC-resurser](../resources/resources.md)
- [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)
