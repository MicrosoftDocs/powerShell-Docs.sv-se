---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 7e87ed4bc9a86be52d4d06d3e87386a1111227c5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686938"
---
# <a name="software-inventory-logging-sil"></a>Loggning av programvaruinventering (SIL)

**VIKTIGT:** *När du installerar WMF 5.0 Windows Server 2012 R2-server som redan kör SIL, är det nödvändigt att köra cmdleten Start-SilLogging en gång när WMF installerat, eftersom installationsprocessen avbryts felaktigt funktionen Software Inventory Logging.*

Loggning av Programvaruinventering bidrar till att minska driftskostnaderna för att få korrekt information om Microsoft-programvara som installerats lokalt på en server, men speciellt över flera servrar i en IT-miljö (förutsatt att programvaran är installerad och körs vår IT-miljö). Förutsatt att något har konfigurerats kan du vidarebefordra data till en aggregeringsserver och samla in loggdata på ett ställe med en enhetlig, automatisk process.

Medan du kan också logga programinventeringsdata genom att fråga datorerna direkt, loggning av Programvaruinventering, genom att använda en arkitektur för vidarebefordran (via nätverket) som initieras av varje server, lösa problem med datoridentifiering som server som är typiska för många Software inventory scenarier och tillgångshantering. Loggning av Programvaruinventering använder SSL för att skydda data som vidarebefordras via HTTPS till en aggregeringsserver. Lagra data i ett och samma ställe tillhandahåller data som är enklare att analysera, hantera och dela när det behövs.

Ingen av dessa data skickas till Microsoft som en del av funktionen. Programvaruinventeringsdata och -funktioner är endast avsedda att användas av serverprogrammets licensierade ägare och administratörer.

Mer information och dokumentation om loggning av Programvaruinventering-cmdlets finns i Windows Server 2012 R2 onlineresurser på <http://technet.microsoft.com/library/dn383584.aspx>.
