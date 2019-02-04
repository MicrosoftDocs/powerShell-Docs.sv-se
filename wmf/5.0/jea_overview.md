---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 0bc085588190f134c4a687c952509aa256b5f840
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687155"
---
# <a name="just-enough-administration-jea"></a>JEA (Just Enough Administration)
Just Enough Administration är en ny funktion i WMF 5.0 som gör det möjligt för rollbaserad administration via PowerShell-fjärrkommunikation.  Det utökar den befintliga infrastrukturen för begränsad slutpunkten genom att låta icke-administratörer att köra vissa kommandon, skript och körbara filer som administratör.  På så sätt kan du minska antalet fullständiga administratörer i din miljö och förbättra din säkerhet.  JEA fungerar för allt som du hanterar via PowerShell; Om du kan hantera något med PowerShell, JEA kan hjälpa dig att göra det mer säkert.  För detaljerad information om Just Enough Administration, Kolla in den [uppleva guiden](http://aka.ms/JEA).

Till skillnad från gamla begränsad slutpunkter är både kraftfulla och enkelt att konfigurera JEA.  Användarfunktioner i JEA kan styras detaljerat, till att begränsa vilka parameteruppsättningar och värden kan anges till ett visst kommando. Användarens åtgärder körs i kontexten för en enstaka virtuellt konto som har behörighet att utföra administrativa åtgärder.  Kommandon som anropas av användaren kan loggas säkerhetsgranskning.

JEA fungerar genom att låta dig skapa speciellt konfigurerad begränsad slutpunkter.  De här slutpunkterna har några viktiga egenskaper:

1. Användare som ansluter till dem ”kör som” ett konto med privilegier virtuella som finns endast för varaktigheten för den här fjärrsessionen.  Som standard det här virtuella kontot är medlem i den inbyggda gruppen Administratörer, samt en Domänadministratörer på domänkontrollanter (Observera: dessa behörigheter kan konfigureras). Genom att ansluta som en användare och som körs som en annan, Privilegierade användare, kan du tillåta icke-privilegierade användare att utföra vissa administrativa uppgifter utan att ge dem administrativa rättigheter på ditt system.
2. Slutpunkten är låst.  Det innebär att PowerShell körningar i nr språkläge.  Endast vissa kommandon, skript och körbara filer visas för användaren.
3. Olika användare som ansluter visas med en annan uppsättning funktioner som är baserade på gruppmedlemskap.  Du kan ange olika roller till olika funktioner på samma slutpunkt.
