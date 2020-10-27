---
ms.date: 06/12/2017
title: Loggning av programvaruinventering (SIL)
description: WMF 5. x Lägg till funktioner för loggning av program varu inventering som gör att du kan samla in information om installerad program vara på en central plats för enklare hantering och granskning.
ms.openlocfilehash: 85e261782a3df5fe5561a80529ba699d686a8779
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646616"
---
# <a name="software-inventory-logging-sil"></a>Loggning av programvaruinventering (SIL)

> [!IMPORTANT]
> När du installerar WMF 5. x på en Windows Server 2012 R2-server som redan kör SIL, är det nödvändigt att Start-SilLogging köra cmdleten en gång efter installationen av WMF, eftersom installations processen felaktigt stoppar funktionen för loggning av program varu inventering.

Loggning av program varu inventering bidrar till att minska drifts kostnaderna för att få korrekt information om Microsoft-programvaran som installerats lokalt på en server, men särskilt på många servrar i en IT-miljö (förutsatt att program varan är installerad och körs i IT-miljön). Som har kon figurer ATS kan du vidarebefordra dessa data till en agg regerings Server och samla in loggdata på ett och samma ställe med en enhetlig, automatisk process.

Även om du även kan logga program varu inventerings data genom att fråga varje dator direkt, kan program varu inventerings loggning, genom att använda en vidarebefordrings arkitektur (över nätverket) som initieras av varje server, lösa Server identifierings utmaningar som är typiska för många program varu inventerings-och till gångs hanterings scenarier. Loggning av program varu inventering använder SSL för att skydda data som vidarebefordras över HTTPS till en agg regerings Server. Att lagra data på en plats gör det lättare att analysera, manipulera och dela när det behövs.

Ingen av dessa data skickas till Microsoft som en del av funktions funktionerna. Loggnings data och funktioner för program varu inventering är avsedda för den enda användningen av serverprogram varans licensierade ägare och administratörer.

Mer information och dokumentation om cmdlets för loggning av program varu inventering finns i [Hantera loggning av program varu inventering i Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
