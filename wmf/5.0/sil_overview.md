---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 4bfedd585958f84889954bd9ee022ea47ac191b2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="software-inventory-logging-sil"></a>Loggning av programvaruinventering (SIL)

** Viktigt: ** *när du installerar WMF 5.0 på en Windows Server 2012 R2-Server som redan kör SIL, är det nödvändigt att köra cmdleten Start-SilLogging en gång efter installationen WMF som installationen avbryts felaktigt programvaran Inventera loggningsfunktionen.*

Software Inventory Logging hjälper till att minska driftskostnaderna för hämtning av korrekt information om Microsoft-programvara som installeras lokalt på en server, men speciellt över flera servrar i en IT-miljö (förutsatt att programvaran är installerad och körs hela IT-miljön). Förutsatt en ställs in kan vidarebefordra data till en aggregeringsserver, och samla in loggdata på ett ställe med en enhetlig, automatisk process.

Medan du kan också logga programinventeringsdata genom att fråga varje dator direkt, kan Programvaruinventering, genom att använda en vidarebefordringsarkitektur (över nätverket) initieras av varje server hantera de server identifiering utmaningar som är vanliga för många Software inventory scenarier och tillgångshantering. Loggning av Programvaruinventering använder SSL för att säkra data som vidarebefordras över HTTPS till en aggregeringsserver. Lagra data i en enda plats gör att blir lättare att analysera, hantera och dela vid behov.

Ingen av dessa data skickas till Microsoft som en del av funktionen. Programvaruinventeringsdata och -funktioner är endast avsedda att användas av serverprogrammets licensierade ägare och administratörer.

Mer information och dokumentation om loggning av Programvaruinventering-cmdlets finns i Windows Server 2012 R2 onlineresurser på <http://technet.microsoft.com/library/dn383584.aspx>.
