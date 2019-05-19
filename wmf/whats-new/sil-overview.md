---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Loggning av programvaruinventering (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856170"
---
# <a name="software-inventory-logging-sil"></a>Loggning av programvaruinventering (SIL)

> [!IMPORTANT]
> När du installerar WMF 5.x Windows Server 2012 R2-server som redan kör SIL är det nödvändigt att köra cmdleten Start-SilLogging en gång efter installationen WMF eftersom installationsprocessen avbryts felaktigt funktionen Software Inventory Logging.

Loggning av Programvaruinventering bidrar till att minska driftskostnaderna för att få korrekt information om Microsoft-programvara som installerats lokalt på en server, men speciellt över flera servrar i en IT-miljö (förutsatt att programvaran är installerad och körs vår IT-miljö). Förutsatt att något har konfigurerats kan du vidarebefordra data till en aggregeringsserver och samla in loggdata på ett ställe med en enhetlig, automatisk process.

Medan du kan också logga programinventeringsdata genom att fråga datorerna direkt, loggning av Programvaruinventering, genom att använda en arkitektur för vidarebefordran (via nätverket) som initieras av varje server, lösa problem med datoridentifiering som server som är typiska för många Software inventory scenarier och tillgångshantering. Loggning av Programvaruinventering använder SSL för att skydda data som vidarebefordras via HTTPS till en aggregeringsserver. Lagra data i ett och samma ställe tillhandahåller data som är enklare att analysera, hantera och dela när det behövs.

Ingen av dessa data skickas till Microsoft som en del av funktionen. Programvaruinventeringsdata och -funktioner är endast avsedda att användas av serverprogrammets licensierade ägare och administratörer.

Mer information och dokumentation om loggning av Programvaruinventering-cmdlets finns i [hantera loggning av Programvaruinventering i Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
