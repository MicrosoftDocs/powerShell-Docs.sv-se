---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Loggning av programvaruinventering (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145161"
---
# <a name="software-inventory-logging-sil"></a>Loggning av programvaruinventering (SIL)

> [!IMPORTANT]
> När du installerar WMF 5. x på en Windows Server 2012 R2-server som redan kör SIL, är det nödvändigt att köra cmdleten Start-SilLogging en gång efter installationen av WMF, eftersom installations processen felaktigt stoppar funktionen för program varu inventerings loggning.

Loggning av program varu inventering bidrar till att minska drifts kostnaderna för att få korrekt information om Microsoft-programvaran som installerats lokalt på en server, men särskilt på många servrar i en IT-miljö (förutsatt att program varan är installerad och körs i IT-miljön). Som har kon figurer ATS kan du vidarebefordra dessa data till en agg regerings Server och samla in loggdata på ett och samma ställe med en enhetlig, automatisk process.

Även om du kan logga program varu inventerings data genom att fråga varje dator direkt, kan loggning av program varu inventering, genom att använda en vidarebefordrings arkitektur (över nätverket) som initieras av varje server, lösa Server identifierings utmaningar som är typiska för många scenarier för program varu inventering och till gångs hantering. Loggning av program varu inventering använder SSL för att skydda data som vidarebefordras över HTTPS till en agg regerings Server. Att lagra data på en plats gör det lättare att analysera, manipulera och dela när det behövs.

Ingen av dessa data skickas till Microsoft som en del av funktions funktionerna. Programvaruinventeringsdata och -funktioner är endast avsedda att användas av serverprogrammets licensierade ägare och administratörer.

Mer information och dokumentation om cmdlets för loggning av program varu inventering finns i [Hantera loggning av program varu inventering i Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
