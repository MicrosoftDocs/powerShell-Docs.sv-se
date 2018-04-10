---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 847bd978b0a8ad8daf26d37ee8759f88fba67f31
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="just-enough-administration-jea"></a>JEA (Just Enough Administration)
Bara tillräckligt Administration är en ny funktion i WMF 5.0 som gör det möjligt för rollbaserad administration via PowerShell-fjärrkommunikation.  Det utökar den befintliga infrastrukturen för begränsad slutpunkten genom att tillåta icke-administratörer kan köra specifika kommandon, skript och körbara filer som administratör.  På så sätt kan du minska antalet fullständiga administratörer i din miljö och förbättra din säkerhet.  JEA fungerar för allt som du hanterar via PowerShell; Om du kan hantera något med PowerShell hjälpa JEA dig att göra så säkrare.  En närmare titt på bara tillräckligt Administration, ta en titt på [upplevelse guiden](http://aka.ms/JEA).

Till skillnad från gamla begränsad slutpunkter är JEA både kraftfulla och enkelt att konfigurera.  Funktioner för användaren i JEA kan styras granularly, till att begränsa vilka parameteruppsättningar och värden kan anges till ett visst kommando. Användarens åtgärder körs i kontexten för en enstaka virtuellt konto som har behörighet att utföra administratörsåtgärder som.  Kommandon som anropas av användaren kan loggas säkerhetsgranskning.

JEA fungerar genom att låta dig skapa särskilt konfigurerat begränsad slutpunkter.  Dessa slutpunkter ha några viktiga egenskaper:

1. Användare som ansluter till dem ”kör som” en virtuell konto med privilegier som finns bara för varaktighet för den här sessionen.  Som standard virtuella kontot är medlem i den inbyggda gruppen Administratörer, samt en Domänadministratörer på domänkontrollanter (Obs: dessa behörigheter kan konfigureras). Genom att ansluta som en användare och körs som en annan, Privilegierade användare, kan du tillåta icke-privilegierade användare att utföra särskilda administrativa uppgifter utan att ge dem administratörsbehörighet på datorn.
2. Slutpunkten är låst.  Det innebär att PowerShell körs i läget No språk.  Endast vissa kommandon, skript och körbara filer visas för användaren.
3. Olika användare som ansluter visas med en annan uppsättning funktioner som är baserat på medlemskap.  Du kan ange olika roller till olika funktioner i samma slutpunkten.